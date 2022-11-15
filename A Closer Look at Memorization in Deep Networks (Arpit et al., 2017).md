Source: 
Consider: [[]]
Tags: 
______________

# Claim
- DNN optimization of real data vs noise is different
- Learn simple patterns first then memorize
- Regularization can hinder memorization while preserving ability to learn patterns from real data

# Key takeaways
- Real data contains easy and hard patterns.
- 

## Experiments
### Qualitative difference of DNNs trained on random vs. real data
#### Easy examples as evidence of patterns in real data
Hypothesis: 
Some patterns should be easier to learn than others. If this is the case, some examples should be constantly labeled early and others lately. Conversely if the algorithm use a brute-force memorization strategy, every examples should have the same rate of proper labeling. 

Setup:
Training 100 MLPs (with 100 different random initialization seeds) for 1 epoch over the shuffled data and measure the average classification error of each example.

Results: 
- Real data display important difference of classification errors (i.e. some examples are easier to learn than others).
- randX (noisy input) can be modeled as binomial noise
- randY (noisy labels) seems to leverage some shared patterns (does not fully follow a binomial noise model)

#### Loss sensitivity in real data vs random data
Hypothesis:
Brute-force memorization implies important gradient update for each examples. 

Setup:
Measuring the loss-sensitivity $g_\boldsymbol{x}^t = ||\frac{\delta L_t}{\delta \boldsymbol{x}}||$ of each examples averaged over $T$ steps. 

Results:
- Real data: the Gini coefficient of the loss-sensitivity is high (i.e. unequal distribution of sensitivity)
- random data: the Gini coefficient is lower (i.e. most examples have high sensitivity).

If sensitivity is evaluated for each class (like a heatmap) we can see that cross-category patterns are more learned on real data than on random data

#### Capacity and effective capacity
Effects of capacity and dataset size on validation performances

Results: increasing the representational capacity (number of hidden units) does improve the generalization error. This result contradict the theory which state that improving generalization implies to reduce the capacity.

Effects of capacity and dataset size  on training time

Results: 
1. increasing the representational capacity (number of hidden units) reduce the training time more for noise than for real data. This is argued to be a clue that learning patterns (instead of bruteforce memorization) does not benefit much from more expressive capacity.

2. increasing the number of training examples requires more time to convergence for noisy data than real data. This is argued to show that samples from real data already shared common patterns (and do not need more training to be properly labeled) while  noisy data need more training to be memorized by bruteforce.

### DNNs learn patterns first
Use critical samples to investigate decision boundaries differences between real and random data.

Critical samples are data samples which are close to other sample(s) but are not of the same label. This implies that such points are close a decision boundary. The ratio of samples close to decisions boundaries is an indicator of the complexity of the hypothesis (the more complex the hypothesis, the more samples found close to the boundaries).

#### Critical samples throughout training
Results: 
- the number of critical samples is lower in real data than in random data.
- the noisier the less accurate
- the noisier the higher the critical sample ratio
- noisy networks achieve high accuracy on validation set **before** improving on training set loss.

Conclusion: the model learn simple patterns before memorizing.

### Effects of regularization on training
Question: How does regularization changes the training regime?

Results: 
- regularization (especially dropout) can reduce the brute-force memorization process while preserving generalization.
- regularization (especially dropout) limit the speed of memorization.

## Conclusions
- Generalization is not only dependent on the architecture and training procedure but also on the training data itself.
- Regularizer control the speed of memorization.
- DNNs generalize first and then perform brutefore memorization