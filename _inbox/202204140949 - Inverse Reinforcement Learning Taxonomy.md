Previous: [[]]
Source: [[]]
Consider: [[]]
Tags: 
______________

# RL:
Learning the best policy to maximize cumulative reward in a given environment. 
The policy is the mapping $\pi(s_t,a_t) \rightarrow s_{t+1}$. 

- For each state $s_t$ the reward $r_t$ is given.


# Inverse RL:
- The reward $s_t$ is not given. Therefore it must be approximated.

The goal of Inverse Reinforcement Learning is to built good approximation the reward function. 


## Apprenticeship Learning:
Once $\hat{R}$ is build, finding the best policy given $\hat{R}$ is apprenticeship learning. 




-------------------------------------
Learning from humans
-> Imitation based (supervised): behavioural cloning
-> Reward based (RL): learning the reward
	->  Reward modeling: infer from feedback
	-> 
