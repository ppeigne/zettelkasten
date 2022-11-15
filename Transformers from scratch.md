Source: https://e2eml.school/transformers.html
Consider: [[]]
Tags: #transformer
______________

# Claim
Matrix multiplication is a kind of table lookup. 

# Key takeaways
### Matrix multiplication is a kind of table lookup
Having a matrix $A$ made up of a stack of one-hot vectors, the result of $A \cdot B$ can be seen as a table lookup into $B$. 

![[Pasted image 20220713095118.png]]

### Attention
$$\text{Attention}(Q,K,V) = \text{softmax}(\frac{QK^T}{\sqrt{d_k}})V$$

![[Pasted image 20220713100824.png]]

$K, Q, V$ are produced by a linear unit projecting them into a lower-dimension from the original embedding. 

### Skip-connection 
Each layer input is added to its output (and the result is normalized) before being fed to the next layer. 