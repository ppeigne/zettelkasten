Source: https://ai-alignment.com/alphago-zero-and-capability-amplification-ede767bb8446
Consider: [[]]
Tags: #ida #amplification #distillation #alphago_zero
______________

AlphaGo Zero illustrates very well the process of capabilities amplification. 

Algorithm $A$ is here split into 
- $p$, predicting the most interesting moves
- $v$, evaluation the probability of victory given the current board

Amplification:
$\operatorname{Amplify}^A = \text{MTCS}_{p,v}$

Distillation:
$p_{t+1} \leftarrow \text{MTCS}_{p,v}$
$v$ is updated using the results of the game played by $\text{MTCS}_{p,v}$

-> Problem: we need a way to improve a policy while preserving the alignment.