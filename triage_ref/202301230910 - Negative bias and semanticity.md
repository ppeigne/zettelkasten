Source: 
Consider: [[Toy Models of Superposition]], [[Interim report]]
Tags: #polysemanticity #monosemanticity #negative_bias
______________
[[Toy Models of Superposition]] claims that negative bias are usefull to correct interferences produced by superposition. 
A negative bias transforms a small positive result ($W^{(l)}A^{(l-1)} > 0$) into a negative one ($W^{(l)}A^{(l-1)} + b^{(l)} < 0$) which is then set to zero by being applied a non-linear activation $A^{(l)} = \max(0, W^{(l)}A^{(l-1)} - b^{(l)})$. 

However, [[Engineering monosemanticity]] claims that a negative bias helps with pushing the model toward monosematicity. Their results shows that 
