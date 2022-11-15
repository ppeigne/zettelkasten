Source: https://transformer-circuits.pub/2021/framework/index.html
Consider: [[]]
Tags: #transformer #explainability #circuits
______________

# Claim

## Reverse engineering results

- **Zero layer transformers model bigram statistics.** The process of embedding and unembedding the input tokens can be considered an approximation (compression) of a bigram log-likelyhood matrix. In other words, the operation $W_U W_E \cdot x_{tokens}$ produced an approximation of how likely is a token to appear given the current token.

- **One layer attention-only transformers are an ensemble of bigram and "skip-trigram" (sequence of the form "A... B C") models.** Such models' results can be accessed directly from the weights without running them. We can consider the attention layer to be 'frozen', i.e. looking at the output-value (OV) circuit results while considering the key-querry (KQ) circuit fixed (or doing the reverse operation).

- Two-layer attention-only transformers can implement much more complex algorithms using compositions of attention heads. #FIXME

- One layer and two layer attention-only transformers use very different algorithms to perform in-context learning. #FIXME

## Conceptual take-away

- **Attention heads can be understood as independent operations, each outputting a result which is added into the residual stream.** Instead of considering the attention heads as being concatenated through the operations of the attention block, it brings much more explainability to consider each attention head as completely independent from the others and therefore performing independent end-to-end operations. 
$$
W_O^H 
\begin{bmatrix}
r^{h_1} \\r^{h_2} \\ \dots \\
\end{bmatrix}
=
\begin{bmatrix}
W_O^{h_1}, & W_O^{h_2}, & \dots \\
\end{bmatrix}\cdot\begin{bmatrix}
r^{h_1} \\r^{h_2} \\ \dots \\
\end{bmatrix}
=
\underbrace{\sum_i W_O^{h_i}r^{h_i}}_{\substack{\text{attention heads } h_i \\\text{ applied independently} \\ \text{and added together}}}
$$


- **Attention-only models can be written as a sum of interpretable end-to-end functions.**

- **Transformers have an enormous amount of linear structure.** #FIXME

- **Attention heads can be understood as having two largely independent computations.**
	- $W_{ov}$, the *Output-Value circuit* describes how attending to a given token affects the logits.
	- $W_{QK}$, the *Query-Key* circuit controls which token the head prefers to attend to.

- **Key, query and values vector can the thought of as intermediate results in the computation of the low-rank matrices $W_Q^T W_K$ and $W_O W_V$. It can be useful to describe transformers without reference to them.** Considering directly the low-rank matrices operations is a more expressive manner to investigate the internals of transformers. 

- Composition of attention heads greatly increases the expressivity of transformers. # FIXME

- **All components of a transformer (the token embedding, attention heads, MLP layers and unembedding) communicate with each others by reading and writing to different subspaces of the residual stream.** Each internal elements (Attention heads and MLP layers) read and write from the 'residual stream' by being applied to the residual stream and then added to its original values. $$x_{i+1} = x_i + \text{layer}_i(x_i)$$

_____________________________________


![[Pasted image 20220718114416.png]]

*'The fundamental actions of attention heads is moving information.'*

$W_{ov}$, the *Output-Value circuit* describes how attending to a given token affects the logits.
$W_{QK}$, the *Query-Key* circuit controls which token the head prefers to attend to.

Rewriting the formulas (using tensor products and considering each attention head as independent) allows us to consider the result as a sum of *end-to-end* paths.



# Key takeaways

### Virtual Weights and the Residual Stream as a Communication Channel
Each "residual blocks" (attention head or MLP layer) perform two linear operations ($f(x)=\alpha x + b$) to the residual stream. One while reading, the second while adding its outputs to the residual stream 

#### Virtual weights
Being fully additive linear operations, it is possible to observe how each layer interact with the outputs of previous layers. By multiplying the input matrix $W_I^n$ with a previous layer's output matrix $W_O^{n-m}$ we can observe the hidden connection between them through the residual stream.

![[Pasted image 20220719105324.png]]

#### Subspace and residual stream bandwidth



### Reading and writing to the residual stream




![[Pasted image 20220718114339.png]]

![[Pasted image 20220718204249.png]]


### Matrices $W_Q^T W_K$ and $W_O W_V$ being low-rank 
Dimensions:
- $n_\text{heads} = 12$
- $d_\text{head} = 64$
- $d_\text{model} = n_\text{head} * d_\text{head} = 768$

Maximum rank of an $[n \times m]$ matrix: $\operatorname{min}(n, m)$

The matrices:
- $W_Q^h$, $W_K^h$ and $W_V^h$ are $[d_\text{head} \times d_\text{model}]$, they have a maximum rank of  $\operatorname{min}(d_\text{head}, d_\text{model}) = d_\text{head}$. 
- $W_O^h$ is $[d_\text{model} \times d_\text{head}]$ and have a maximum rank of $d_\text{head}$ as well.


Because of the property of rank, $$\operatorname{rank}(AB) = \operatorname{min}(\operatorname{rank}(A), \operatorname{rank}(B))$$**the maximum rank** the composed matrices $W_{OV}^h = W_O^hW_V^h$ and $W_{QK}^h = W_Q^{hT}W_K^h$ can reach **is $d_\text{head}$ = 64, even if their dimensions are $[d_\text{model} \times d_\text{model}] = [768 \times 768]$.**


### 1L 
Copying / primitive in-context learning
The main operation in 1L transformers is copying: 
- the OV circuit simply increase the probability of having the source token it attends to to be outputted.
- "the QK circuit then only attends back to tokens which could plausibly be the next token"


### Eigenvector and eigenvalue analysis
| |Negative eigenvalues|Imaginary eigenvalues|Positive eigenvalues| 
|-|-|-|-|
|**OV circuit** |Anti-copying|Different tokens|Copying| 
|**QK circuit** |Avoid same tokens|Different tokens|Attend to same tokens| 

Other options:
- Look at the diagonal tells how much a token is reacting (i.e. willing to 'copy') to itself.
- 'How often a random token increases its own probability more than any other token (or is one of the k-most increased tokens)'
'It's worth noting that all of these potential notions of copying are linked by the fact that the sum of the eigenvalues is equal to the trace is equal to the sum of the diagonal.'


# 2L
Composition implies that the current attention matrix reads in a subspace affected by a previous head.
- Q-Composition 
- K-Composition
- V-Composition: correspond to virtual attention heads

Q and K compositions produced complex attention patterns (not reducible to simple composition such as V-Composition)
V-Composition acts as a "virtual attention head", i.e. composition of information's movements is still information's movement.

### Induction heads
Induction heads use composition to be able to look for a previous occurrence of the given token and then to predict the next token found after the previous occurrence as the next token to output. 
"
-   One layer model copying head: 
	- `[b] … [a] → [b]`:  `[ perfect] ... [ are] → [ perfect]`
	- `[b] … [a] → [b']`: `[ perfect] ... [ looks] → [ super]`
	
	-   And when rare quirks of tokenization allow: 
			- `[ab] … [a] → [b]`: `[Ralph] ... [ R] → [alph]`
			- `[ab] … [a] → [b']`: `[Ralph] ... [ R] → [ALPH]`

-   "Two layer model induction head: 
	- `[a][b] … [a] → [b]`: `[ Pot][ters] ... [ Pot] → [ters]`

![[Pasted image 20220719155213.png]]

'The minimal way to create an induction head is to use K-composition with a previous token head to shift the key vector forward one token'

Induction heads should have:
- "a 'copying' OV circuit matrix"
- "a 'same matching' QK circuit matrix associated with the $\text{ID} \otimes A^{h_{-1}} \otimes W$ term", "where $A^{h_{-1}}$ denotes attention pattern attending to the previous token" 
