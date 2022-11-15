Previous: [[]]
Source: [[]]
Consider: [[]]
Tags: 
______________

The point is to learn to approximate $Q$. 

A naive approach would be: 
- define a neural net $Q$ with parameters $\theta$.
- train $Q$ with the following training signal:
$$\hat{y}_j = Q(\phi_j, a_j ; \theta)$$
$$y_j = 
    \begin{cases}
        r_j & \mbox{if episode terminates at step } j+1 \\
        r_j + \gamma \max_{a'} Q(\phi_{j+1}, a'_j ; \theta)  & \mbox{otherwise}
	\end{cases}
$$
	
The problem with that approach is two-fold:
1. **The data is not *iid*.** You get strongly correlated samples because $\phi_{j+1}$ is a results of $a^{*}_j = \operatorname*{argmax}_a Q(\phi_j, a_j ; \theta)$.

	-> Solution: using a memory buffer. 

2. It is hard to update $Q$ because **$Q$ is used to generate both $y$ and $\hat{y}$.**  
 
	-> Solution : use a target network $\hat{Q}$ to generate $y_j$. $\hat{Q}$ is a copy of $Q$ updated any $n$ steps. 