Source: https://arxiv.org/abs/1509.06461
Consider: [[Human Level Control Through Deep Reinforcement Learning (Mnih, V., Kavukcuoglu, K., Silver, D. et al), 2015]]
Tags: #Q_learning #deeplearning #reinforcement_learning
______________
The authors propose an update of the DQN based on (tabular) double Q learning. The main objective is to limit the overestimation of conventional DQN.

### Overestimation problem
In DQN $\hat{Q}_\theta^-$ is used both for action selection and evaluation in the target equation: 
$$
Y_t = R_{t+1} + \gamma \max_{a'} \hat{Q}(S_{t+1}, a'; \theta^-_t)
$$

The max operator selects the actions after evaluating them with  $\hat{Q}_{\theta^{-}}$.

This can lead to overestimation because the $\max$ operator will select  overestimated values (the biggest one). Then the overestimated target will be used to update the Q function, leading to higher overestimation in the future.

### Solution
The proposed solution is to decouple the selection from the evaluation in the target equation. 

This can be done thanks to the following equality:
$$
\begin{array}{cc}
\max_{x} f(x) & = & f(\operatorname*{argmax}_{x} f(x)) \\
\\
\max_{a'} \hat{Q}(S_{t+1}, a'; \theta^-_t) & = &\hat{Q}( \operatorname*{argmax}_{a'} \hat{Q}(S_{t+1}, a'; \theta^-_t); \theta^-_t)
\end{array}
$$

Then, we replace $\hat{Q}(S_t, a'; \theta^-_t)$ by $Q(S_{t+1}, a' ; \theta_t)$ to decouple the evaluation (done with $\hat{Q}_{\theta^{-}}$) from the selection (done with $Q_\theta$)

$$
\begin{array}{ll}
	Y_t  & = & R_{t+1} + \gamma \max_{a'} \hat{Q}(S_{t+1}, a'; \theta^-_t) \\
	& = & R_{t+1} + \gamma \hat{Q}(\operatorname*{argmax}_{a'} Q(S_{t+1}, a' ; \theta_t); \theta^-_t)
\end{array}
$$ 

The evaluation is still done using $\hat{Q}_{\theta^{-}}$, but the selection of the best actions is done using $Q_\theta$ for calculating the target.
