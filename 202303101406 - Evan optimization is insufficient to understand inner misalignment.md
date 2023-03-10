Source: [[Risks from learned optimization (Hubinger et al., 2019b)]]
Consider: [[]]
Tags: #mesa-optimization #optimization #implicit_search #heuristics
______________
Mesa optimization brings the focus on internal search (as optimization_Evan).
But what we care about is the configuration target of the model (considered as an optimizing system): if this configuration target is not the one we want, then the model is (inner) misaligned.

If the model is performing some internal search then we can indeed try to understand what kind of explicit objective function it uses to drive its search process. 

However, a model can reach very bad configuration target without performing any internal search using explicit objective function, by relying on heuristics. 