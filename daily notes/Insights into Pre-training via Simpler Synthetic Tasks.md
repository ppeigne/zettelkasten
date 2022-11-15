Source: https://arxiv.org/abs/2206.10139.pdf
Consider: [[]]
Tags: #synthetic_dataset #pretraining
______________

# Claim
- LIME Synthetic pre-training methods is able to reach up to 67% of the performances of a natural pre-training (benchmarked on 6 tasks).
- Almost equivalent to LIME performances (65%) can be reach by working on a simple synthetic task: 'Set'. The goal of this task is to de-duplicate the input: e.g. "a, a, a, b, c, c"  -> "a, b, c". 
- 39% of the pre-training benefits can be reach by initializing the models using the parameter statistics of the pre-trained model.

# Key takeaways
