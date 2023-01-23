Source: 
Consider: [[Toy Models of Superposition]], [[Interim report]], [[Engineering monosemanticity]]
Tags: #polysemanticity #monosemanticity #negative_bias
______________
[[Toy Models of Superposition]] claims that negative bias are usefull to correct interferences produced by superposition. 
Indeed, a negative bias can transform a small positive result ($W^{(l)}A^{(l-1)} > 0$) into a negative one ($W^{(l)}A^{(l-1)} + b^{(l)} < 0$) which can then be set to zero by being applied a non-linear activation $A^{(l)} = \max(0, W^{(l)}A^{(l-1)} - b^{(l)})$. 

However, [[Engineering monosemanticity]] claims that a negative bias helps with pushing the model toward monosematicity. Their results shows that models initialized with a negative bias find monosemantic local minima for every learning rates while those initialized with zero mean bias converge toward monosemantic local minima for only a fraction of the learning rates (i.e. the higher ones).

These findings seem contradictory: if negative bias help working in a superpersition, why does models initialized with negative bias converge toward monosemantic local minima?

