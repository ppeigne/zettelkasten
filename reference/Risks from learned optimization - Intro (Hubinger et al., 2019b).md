### [https://www.alignmentforum.org/posts/FkgsxrGf3QxhfLWHG/risks-from-learned-optimization-introduction | Risks from learned optimization - intro]

An optimizer system can have: 
	-  a purpose : what it is optimized to do. Its designers objectives.
	- a goal : what it optimizes for. Its own objectives. (hypothetical)
	
Optimizer: 
*a system is an _optimizer_ if it is internally searching through a search space (consisting of possible outputs, policies, plans, strategies, or similar) looking for those elements that score high according to some objective function that is explicitly represented within the system*

Need to run a optimization algorithm to maximize its objectives. 

**Neural nets are usually not optimizer.  They are optimized to achieve their optimizer's purpose. The learning algorithm which train them is.**

NN could become optimizer as well. In such case they are meta-optimizer or mesa-optimizer.

- Meta-optimizer : optimizer explicitly designed to produce an optimizer. E.g. helping tune the main optimization. Hyper-parameters tuning is a good example of meta-optimization.

- Mesa-optimizer: ML system turned out to be an optimizer as a results of its own optimization process without being explicitly designed for that purpose. The production of an inner mesa-optimizer by the base optimizer is the result of its own optimization process because it is "instrumentally useful" for solving its task.

- Base optimizer :  an optimizer created to optimize an ML system.

- Learned algorithm : any algorithm produced by a based optimizer.

 
Mesa-optimizer are not sub-systems or sub-agents. 
A mesa-opt NN is just an NN implementing an optimizing process internally. 

Behavior objective: what appears to be the objective.
Mesa-objective: the actual objective of the mesa-optimizer.

A risk arises from (common) distributional shifts because where the mesa-optimizer will more robustly optimize for its mesa-objectives.

Evolution example:
Evolution as a base opt. selected organism based on the obj. function of their fitness in their env. 
Biological organisms like plants only implement the heuristics that have been preselected by evolution. They do not have inner goals.

Humans can have behavior completely different from what the evolution selected them for. They have goal-directed optimization algorithm in their brains, and behave according to that : they optimize their own objectives functions (without caring of evolution's one!). Hence, human mesa-optimizer are not aligned with evolution.

Another example?

#### inner & outer alignment
Outer alignment : eliminate the gap between the base objective and the programmers' goal. Make the objective function fit the real goal (MIDAS problem?). 

Inner alignment: eliminate the gap between the base obj. and the mesa-obj.

Example ?

#### robust vs pseudo-alignment

Robustly aligned mesa-opt. keep performing well according to the base objective even after training (distributional shift etc)

Pseudo-aligned mesa-opt performs well on the training data only. Once not in training it behavior does not fit its base objective. 

Example : 
Being trained on maze navigation trough only red doors and tested in maze with blue doors and red objects inside.
- Robust : navigate without problems through blue doors
- Pseudo-aligned : navigate through the maze and try to reach red objects

####  safety pbs
Two problems 

- Unintended optimization: mitigate situations where mesa-optimization could occurs
- Inner alignment: pseudo-aligned or deceptive alignment. 


##### Precision on mesa-optimizer
*"Whether a system is an optimizer is a property of its internal structure—what algorithm it is physically implementing—and not a property of its input-output behavior. Importantly, the fact that a system’s behavior results in some objective being maximized does not make the system an optimizer. [...] 
[I]mage-classifying neural networks are optimized to achieve low error in their classifications, but are not, in general, themselves performing optimization."*

*"However, it is also possible for a neural network to itself run an optimization algorithm. For example, a neural network could run a planning algorithm that predicts the outcomes of potential plans and searches for those it predicts will result in some desired outcome.[[1]](https://www.alignmentforum.org/s/r9tYkB2a8Fp4DN8yB/p/FkgsxrGf3QxhfLWHG#fn-rdp4gb6fGD36iDTkT-1) Such a neural network would itself be an optimizer because it would be searching through the space of possible plans according to some objective function."*

According to this, any kind of **internal** search through the space of possible plans IS mesa-optimization.