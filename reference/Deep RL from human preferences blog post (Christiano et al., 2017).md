Source: https://openai.com/blog/deep-reinforcement-learning-from-human-preferences/
Consider: [[Learning to summarise with human feedback blog post (Stiennon et al., 2020)]]
Tags: 
______________

#### Reward modeling 

![[Pasted image 20220224114823.png]]

The reward predictor build a representation/model of the reward function from the human feedback.

Then the RL algorithm learn to achieve the goal represented by the reward model. 

Problem : incentive the model to have a behavior which **looks** good.