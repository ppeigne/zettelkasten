Source: https://ai-alignment.com/the-reward-engineering-problem-30285c779450
Consider: [[Directions and desiderata for AI alignment (Christiano, 2017)]]
Tags: #reward_learning #imitation_learning #irl #preferences #feedback
______________

Three possible approaches:
1. Direct supervision: H rate A. 
	Pb: A can be well informed about its actions while H is not. A can have a hidden bad behavior (make use of blind spots) difficult to detect. 
	
	Example of plagiarism: A is supposed to learn to produce new content but it is very difficult to make sure it is not making a copy of original unknown content.

	-> Possible solution: transparency.

2. Imitation learning: A lean to imitate H
	Pb1: how to "dumb-scale" H if H >> A? 
	-> Meeting halfway
	
	Pb2: blind spot problem (cf. above) : how to detect plagiarism? 

3. IRL: infer a reward function based on H behavior and then train A with it
	Pb1: missing information out of H trajectories
	Pb2: close to direct supervision (with same problems) one the reward function is learned
	