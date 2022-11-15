Source: https://arxiv.org/abs/2002.04833
Consider: [[]]
Tags: 
______________

Reward learning source of information
-> demonstration: IRL
-> comparison: reward modeling
-> grounding instructions
-> Leaks: 
	-> turning off
	-> current state of the world

"Human behavior is a reward-rational implicit choice - a choice from an implicit set of options, which is approximately rational for the intended reward".

Recipe for understanding:
1. (implicit) set of options
2. grounding function mapping these options to robot behavior

This recipe is obvious in case such as comparison but not so obvious with other source of information like turning the robot off.

E.g. turning the robot off:
Options : OFF / do nothing
Grounding function: by turning OFF, we inform the robot that we prefer the trajectory where we switch it OFF -> we prefer that it does nothing to acts as it was suppose to.
The robot can then compare the two trajectories

**Warning**: in this part of the text the author use "doing nothing" for the robot AND the humans which can be misleading.



### Designing a new feedback recipe
- Define the implicit (or sometimes explicit) set of options $C$
- Define how those options ground trajectories $\psi(c^*)$
-> Use Equation 1 to get a formal model of human feedback 

$$
\mathbb{P}(c^*| r, C) = \frac{\exp(\beta \cdot \mathbb{E}_{\xi \sim \psi(c^*)}[r(\xi)])}{\sum_{c \in C}\exp(\beta \cdot \mathbb{E}_{\xi \sim \psi(c)}[r(\xi)])}
$$
constraint on 
$$
\begin{array}{cc}
	r(\psi(c^*)) \geq r(\psi(c)) & & \forall c \in C
\end{array}
$$

where $\psi(c^*)$ is the grounding function and $C$ the set of choices. 



