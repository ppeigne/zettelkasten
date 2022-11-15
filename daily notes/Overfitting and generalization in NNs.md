- NNs do overfit their training data
- They still performs well over test data (why?)
- The regularization methods:
	- do not improve the generalization 
	OR
	- do not reduce the overfitting

**Need for a measure of difference between the train and test data (how much does the model have to generalize?)**



________________
Investigation of implicit planing:

- Injected "no-op" improved perf -> more time to compute/plan
- Equivalent to this for
	- Alphago: feeding n-time the input to the model?
	- GPT-X: 
	- Reinjecting the input into the residual stream 
		- 