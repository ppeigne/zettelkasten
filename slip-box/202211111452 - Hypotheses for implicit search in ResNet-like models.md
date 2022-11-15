Previous: [[]]
Source: [[]]
Consider: [[]]
Tags: #implicit_search #alphago #experiment
______________

Hypothesis 1: Refinement (i.e. analytical research) 
- Iteratively refine by calculating (e.g. applying threat filters)
	- Logit-lens like
	- Deep dream
- Less sensitive to perturbation

Hypothesis 2: Parallel exploration
- Store candidates moves into specific channel 
	- Causal tracing
- Very sensitive to perturbation (ablation like causal tracing)

Hypothesis 3: H1 + H2 

### Channel stability
We could expect having relative stability among the channels storing the information. Information could potentially be moved along layer but it seems sub-optimal to perform search that way (the residual stream should instead enforce stability of the same type of information) 