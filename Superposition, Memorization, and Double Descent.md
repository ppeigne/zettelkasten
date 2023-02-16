Source: https://transformer-circuits.pub/2023/toy-double-descent/index.html
Consider: [[]]
Tags: #superposition #memorization #generalization #double_descent
______________

# Key takeaways
- Overfitting consist in using superposition to store "data-point features" instead of "generalization features"
- Wether a model store "data-point features" or "generalization features" depends of the dataset size. 
- The double descent phenomenon correspond to the phase change between the "data-point features" and "generalization features" regimes.

### Data-point features
Data-point rather than features are represented as polytopes! This appens when the dataset dimension are small. 

![[Pasted image 20230216110619.png]]

### Double descent

![[Pasted image 20230216110657.png]]