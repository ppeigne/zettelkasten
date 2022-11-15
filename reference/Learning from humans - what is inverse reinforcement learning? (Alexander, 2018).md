Source: https://thegradient.pub/learning-from-humans-what-is-inverse-reinforcement-learning/
Consider: [[]]
Tags: #irl #learning_from_teacher 
______________

# Inverse Reinforcement Learning
Learning from a **human example first**. 
- Difference with behavior cloning : 
	- In BC, we try to produce the same exact output from the human example.
	- In IRL, we try to understand/extrapolate the implicit rules from a human example.
	
- Difference with reward modeling:
	- In RM, we try to understand/extrapolate the implicit rules/reward func. from human feedback. The AI acts and then its actions are rated (through different kind of grading process) by a human operator. 
	- In IRL, we try to understand/extrapolate the implicit rules from a human example. The human acts first and the reward model is produced from it.
	
	**the reward function, rather than the policy, is the most succinct, robust, and transferable definition of the task**,” (Ng, Russel)
	
	The difficulty is to be sure the correct reward func is built. Because the same policy could arises from different rew. func. 
	
		
	
