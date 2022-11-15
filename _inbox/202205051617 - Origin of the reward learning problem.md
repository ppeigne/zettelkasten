Previous: [[]]
Source: [[Reward-rational (implicit) choice - A unifying formalism for reward learning (Jeon, Milli & al. 2020)]]
Consider: [[]]
Tags: #reward_learning #reinforcement_learning 
______________

The training signal for Deep Q-Learning is based on the following equation (or a variation of it):
$$
	y_j = 
    \begin{cases}
        r_j & \mbox{if episode terminates at step } j+1 \\
        r_j + \gamma \max_{a'} \hat{Q}(\phi_{j+1}, a'_j ; \theta^-)  & \mbox{otherwise}
	\end{cases}
$$

where:
- $r_j$ is the reward received at $j$ 
- $\gamma$ is a learning rate #FIXME
- $\hat{Q}$ is the target network used to approximate the Q function
- $\phi_j$ is state of the environment at $j$
- $a'$ is an action performed by the agent in the environment state $\phi_j$


But how do you handle the case when $r$ is not given?

The reward learning algorithms' family tries to learn $r$ from the information present in the agent environment.


