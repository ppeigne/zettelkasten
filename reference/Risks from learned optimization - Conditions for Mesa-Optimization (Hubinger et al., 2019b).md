https://www.alignmentforum.org/s/r9tYkB2a8Fp4DN8yB/p/q2rCMHNXazALgQpGH

#### The task
##### Better generalization through search
Finding a best performing policy need to be able to discriminate through the available policies. The discrimination process implies optimization (as running a planning algorithm to predict the outcomes of those policies).
	
Expansion of the optimization power:
- base optimizer : selection of "highly tuned learned algorithm". Favored by more computational power in training than in running.
- mesa-optimizer: selection of 'higly tuned actions' at the level of the learned algorithm. Favored by more compute in running. 

AlphaZero integrates an hard-coded optimization process working at the level of the learned algorithm (besides not being learned by itself). 


**Search-based strategies are attractive option to reach generality in context of diverse environment. Search allows to find the best actions for each specific instance of the task. **

- base optimizer : "design heuristic that will hold regardless of what task instance the algorithm encounters". Optimization at training only. 
- mesa-optimizer : "determine the best action for a given task instance". Immediate optimization. Immediate adjustment. Better if any new task is novel due to environment diversity.

The bigger the number of different task instances, the more efficient it became to use mesa-optimization.  


##### Compression of complex policies
Compressed policies have lower complexities, which is usually favored by optimization algorithms. E.g. it is shorter to describe a tree searching algorithm than to encode any possible policies for a computer chess algorithm.

##### Task restriction 
Highly restricted task could tamper the arising of mesa-optimizer. Because it involves a less 

##### Human modeling
