Source: https://arxiv.org/pdf/2105.14111.pdf
Consider: [[]]
Tags: #goal_misgeneralization #reinforcement_learning #actor_critic
______________

# Claim
It is possible to detect goal misgeneralization by observing the saliency map of the value functions of actors and critics. By doing so it is possible to show that an agent is misaligned

# Key takeaways
Generalization failure:
- Capability generalization failure
- Goal misgeneralization 

Diversity help alleviating goal misgen

Actor and critic can learn different proxy goals
	- Critic approximated a value function "touch the wall at the end"
	- The actors approximated a goal "go right"