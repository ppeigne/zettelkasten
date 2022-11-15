Previous: [[]]
Source: [[]]
Consider: [[]]
Tags: 
______________

Q Learning suffers from several limitations:
1. Tabular Q learning
-> requires huge memory spaces to track down any possible combinations of states and actions.
-> become completely intractable in continuous environment

2. Parameterized Q learning
-> need a function for Q
	-> handcrafted (human-centric approach, bad idea)
	-> approximation
		-> linear approximation are limited in what they can do
		-> non-linear (deep learning based) approximations did not seems to work at first sight