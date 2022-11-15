Source: https://web.stanford.edu/class/psych209/Readings/MnihEtAlHassibis15NatureControlDeepRL.pdf
Consider: [[Approximate Q-learning]]
Tags: #Q_learning #deeplearning  #reinforcement_learning
______________

The authors start the era of Deep Q Learning (i.e. using Deep NN to learn a parameterized Q value function) by solving the major problems encountered by non-linear approximators in RL until then.

The major contribution are two-fold:
1. The experience replay
2. The target network

### Experience replay
Instead of learning online from current state observations, observations are stored into a memory buffer and then randomly sampled from it as a learning batch.

-> By doing this, the data can be "de-correlated" (each example is not temporally/causally linked to the previous one).

### Target network
The deep Q net replaced by two neural nets: a value network and a target network. 

- **Value network $Q$ with parameters $\theta$:**
	The value network is used to 
	1. select best action  $a^{*}$ while playing:
$$a^{*}_j = \operatorname*{argmax}_a Q(\phi_j, a_j ; \theta)$$
	2. approximate the Q value of the current state $\phi$ given the action $a$ while learning:
	$$\hat{y}_j = Q(\phi_j, a_j ; \theta)$$
	
	The value network performs online learning (i.e. is updated at every steps using experience replay).
	
	
- **Target network $\hat{Q}$ with parameters $\theta^-$:**
	Learning targets are calculated using the target network. 
	
	$$y_j = 
    \begin{cases}
        r_j & \mbox{if episode terminates at step } j+1 \\
        r_j + \gamma \max_{a'} \hat{Q}(\phi_{j+1}, a'_j ; \theta^-)  & \mbox{otherwise}
	\end{cases}$$
	
	The target net is updated by copying the current parameters $\theta$ of the value network every n steps.  
	
-> By doing this the learning process is not "chasing its own tail".