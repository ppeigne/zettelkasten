# Understanding neural network misalignment
## Ngo papers' suggestion:
#### Current important concepts/problems
- [[Scaling Laws for Transfer, (Hernandez et al., 2021)]]
	- [[Learning Curve Theory (Hutter, 2021)]]
	- [[Scaling laws of recovering Bernoulli (Cho, 2021)]]
- [[A Closer Look at Memorization in Deep Networks (Arpit et al., 2017)]]
- [[Deep Double Descent: Where Bigger Models and More Data Hurt, (Nakkiran et al. 2019)]]
- [[The Lottery Ticket Hypothesis: Finding Sparse, Trainable Neural Networks (Frankle et al., 2019)]]
- [[Real World Games Look Like Spinning Tops (Czarnecki et al., 2020)]]
- [[An Empirical Model of Large-Batch Training (McCandlish et al., 2018)]]
	- [[Which Algorithmic Choices Matter at Which Batch Sizes? Insights From a Noisy Quadratic Model (Zhang et al., 2019)]]

#### Exercises
- [[Alignment research exercises (Ngo, 2022) ]]

## Ngo agenda
- [[The alignment problem from a deep learning perspective (Ngo, 2022)]]
- [[Some conceptual alignment research projects (Ngo, 2022)]]

## Papers
#### Implicit search
- [[An investigation of model-free planning (Guez et al., 2019)]]

#### Generalization
- [[Understanding deep learning requires rethinking generalization (Zhang et al., 2016)]]
- [[More Than a Toy: Random Matrix Models Predict How Real-World Neural Representations Generalize (Wei et al., 2022)]]
- [[To understand deep learning we need to understand kernel learning (Belkin et al., 2018)]]
- [[Uniform convergence may be unable to explain generalization in deep learning (Nagarajan & Kolter, 2021)]]
- [[Generalizing from a few environments in safety-critical reinforcement learning (Kenton et al., 2019)]] #owain_evans

Lectures:
- [[Lecture Notes for STAT240 (Robust and Nonparametric Statistics) (Steinhardt, 2021)]]: #training_robustness, #distributional_shift, #non_parametric_modeling:
- [[Advanced Lectures on Machine Learning (Bousquet, 2003)]]


## Misalignment in deep neural networks
Can we ground abstract concepts from [theoretical AGI safety](https://www.alignmentforum.org/s/mzgtmmTKKn5MuCzFJ) in the [context of modern deep learning](https://www.alignmentforum.org/posts/KbyRPCAsWv5GtfrbG/the-alignment-problem-from-a-deep-learning-perspective)? This research agenda aims to improve clarity on the key ideas from high-level discussions about misalignment and make AI safety more accessible to ML researchers. It focuses on reasoning about neural networks that are capable of implicitly learning a range of important skills, and how they might be trained and deployed.

5. A paper which defines the concepts of implicit planning, implicit value functions, implicit reward models, etc, in ML terms. Kinda like [[A General Language Assistant as a Laboratory for Alignment (Askell et al., 2021)]] but more AGI-focused. I want to be able to ask people “does GPT-3 choose actions using an implicit value function?” and then be able to point them to this paper to rigorously define what I mean. I discuss this briefly in the [phase 1 section here](https://www.lesswrong.com/posts/KbyRPCAsWv5GtfrbG/what-misalignment-looks-like-as-capabilities-scale).

## Problem 4 (Ngo)
*Some applications of neural networks use **explicit search algorithms** (like MCTS, used for AlphaGo). But we can also imagine a **large neural network itself learning to implement some kind of search algorithm internally** (which I’ll call implicit search). 
Describe some ways in which we should expect implicit search algorithms to differ from explicit search algorithms. What might persuade us that current models have or haven’t learned to do implicit search? (Again, feel free to give very speculative answers.)*

### In which way implicit search might differ from explicit search? 

### What might persuade us that current models have or haven't learned implicit search?
- [[Mastering the game of Go without  human knowledge (Silver et al., 2017)]]
	- Raw neural has an impressive ELO score. Can it be pure memorization?
- Memory I/O:
- [[Residual Connections Encourage Iterative Inference (Stanisław, et al.2018)]]
- [[Highway and Residual Networks learn Unrolled Iterative Estimation (Greff, 2017)]]
- [[Towards Understanding Residual Neural Networks (Zeng, 2019)]]
	- Some ResNet can be considered as RNN (but not the case in practice): [[Bridging the Gaps Between Residual Learning, Recurrent  Neural Networks and Visual Cortex (Lio and Poggio, 2016)]]
	- The skip-connection brings possibility for reading/writing data in transformers.
		- What are the limitations? (no loop cycles?)