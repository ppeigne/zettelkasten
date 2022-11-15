Source: https://www.alignmentforum.org/s/EmDuGeRw749sD3GKd/p/HqLxuZ4LhaFhmAHWk
Consider: [[]]
Tags: #ida #amplification #distillation 
______________

Given a human expert $H$, an agent $A$, an amplification procedure $\operatorname{Amplify}(H, A)$, and a distillation procedure (training).

$$
\begin{array}{ll}
\text{repeat until convergence:}\\
& A_{t+1} \leftarrow \operatorname{Distill}(\operatorname{Amplify}(H, A_t)) &
\end{array}
$$

AlphaGo Zero is a good example: 
- amplify step is the MCTS
- distillation is the training of the agent on the results of the MCTS

### General properties required for IDA to works:
1. The distillation robustly preserves alignment
2. The amplification robustly preserves alignment
3. At least some human experts are able to iteratively apply amplification to achieve arbitrarily high capabilities at the relevant task