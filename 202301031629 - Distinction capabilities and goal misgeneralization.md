Source: 
Consider: [[Goal misgeneralization in deep Reinforcement Learning (Langosco et al., 2021)]]
Tags: #misgeneralization #goal_misgeneralization #capabilities_misgeneralization
______________
The use of "misgeneralization" or "generalization failure" does not seem to do fit capacities and objective symmetrically. 

#### Problems
1. How to distinguish between competent and "seemingly competent" capabilities/goal
	- Competent: correct objective/capa but splintered OOD (e.g. harvesting food in an alien jungle: you can be a good food harvester on earth, what does food mean in this alien world?)
		- In this case, true obj/capa will fail as well.

	- Seemingly competent: incorrect objective/capa (proxies) which are discovered while OOD.
		- In this case true obj/capa wont.



| |Capabilities|Goal|
|-|-|-|
|Competent |Competently navigate the level toward the target|The coin|
|Proxy |Competently navigate the level if the color do not change a bit|The rightmost wall|




| |Capabilities|Goal|
|-|-|-|
|Training |The model behave competently in training| The model goal is a proxy|
|Eval | ... but fail to behave competently OOD| ... which does not work OOD|
