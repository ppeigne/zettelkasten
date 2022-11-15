Previous: [[]]
Source: [[]]
Consider: [[]]
Tags: 
______________
TL;DR 
- Overparametrized networks are able to generalize well instead of overfit their training data. This surprising phenomenon contradicts the predictions of the classical statistical learning theory and is still cry out for an explanation.

- Several hypothesis could explain why generalization works well in neural nets:
	- Bounded capacities and implicit regularization:  models' capacities are constrained by some empirical (implicit regularization processes) or theoretical (generalization bound) phenomenons and therefore limit their capacity to memorize.
	- Flatness of the loss landscape: the flat minima are easier to find and are supposed to be good for generalization
	- Hyper-dimensional volume of local minima: generalization is easier in wide local minima and wide local minima have a volume so much bigger in the hyper-dimensional loss landscape (the blessing of dimensionality) than sharp minima that it is extremely unlikely for a stochastic optimization process to land in any sharp minima
	- Lottery ticket hypothesis: the initialization lottery can bring good initial settings for efficient (i.e. "winning tickets") sub-networks to be selected by the optimization process.  The overparametrization allows for a lot of tickets to be tried and good generalization capabilities requires only a few winning subnets to arise. 

## Why is it surprising, from the perspective of classic machine learning, that neural nets work so well? 
Overparametrized network can generalize.
Overparametrized neural nets (i.e. models with more parameters than training examples) can have very good generalization error (i.e. performance on the validation set).
Based on the classic machine learning perspective such overparametrized models should overfit their training data instead of learning to generalize, and therefore perform poorly on the validation set. For instance ResNet18 (11M parameters) and was trained on the ImageNet dataset (1.2M samples) and performs very well (3.57% test error). These impressive results are a theoretical conundrum. *Today, this conundrum could be obfuscated by the fact that Large Language Models are not overparametrized (e.g. GTP3 has 175B parameters and was trained on a 499B tokens dataset) but this state of affairs does not change the fact that we still do not understand why overparametrized networks generalize so well.*

## And why do they work so well?

1. Bounded capacities and implicit regularization: 
Several approaches suggest that models' capacities are constrained by some empirical (implicit regularization processes) or theoretical (generalization bound) phenomenons and therefore limit their capacity to memorize.
However, experiments by Zhang et al (2017) training models on random noise have shown that neural nets are indeed able to learn their entire dataset even in a regularized setting (i.e. under explicit regularizer constraint). These findings challenge the idea of bounded capabilities limiting the memorization and also of the role of explicit regularization in learning to generalize.  

Other intriguing findings of Arpit et al. (2017) bring some light (and new questions) on the learning process:  neural nets start with learning simple patterns in the data and rely on brute-force memorization only if the common patterns are insufficient to classify the data. 
A consequence of this (implicit in Zhang et al. (2017), but extensively investigated by Arpit et al. (2017)) is that the representational capacities of neural nets are data-dependent : neural nets "adjust" their capacities based on the degree of complexity required to fit the data. They act as having lower capacities in presence of real-data sharing commons patterns but leverage their full representational capacities if required to (over)fit random data. 
This adaptive adjustment of capacities looks like a model under regularization constraint, from an intuitive point of view. Can it be related to the phenomenon of "double descent"  (cf. Belkin et al. (2018) [Warning: I did not read this paper in depth]) where the model learn first a pattern before interpolating the entire data? 

(Warning: I did not investigate the further hypotheses as deep as I did for the first one. Those explanations unfortunately are much shallower and less grounded.)

2. Flatness of the loss landscape: 
The flat minima are easier to find using stochastic gradient descent (gradient descent optimization is claimed to have an inductive bias toward flat minima) and such minima are supposed to be good for generalization. Indeed flatness increase generalization because it allows more variations of the latent representations to be still captured as patterns. The sharper the minima the less it is able to fit the variations present among the data: if the minima is sharp any tiny difference in the latent space can result in a high loss while still being very close to the configuration lying at the bottom of the minima.    
However (Dinh et al. (2017)) argue that flatness is not a good explanation for generalization: it is possible via reparametrization to produce sharp minima which generalize as well.

3. Hyperdimensional volume of local minima: 
Generalization is easier in wide local minima (an argument close to the previous one). Wide local minima have a volume so much bigger in the hyper-dimensional loss landscape than sharp minima that it is extremely unlikely for a stochastic optimization process to land in any sharp minima. This phenomenon is coined as the "blessing of dimensionality" by Huang et al. (2019) : the higher the dimensions, the more extreme the difference in term of volume. Modern neural networks have a dimensionality so huge that it is statistically almost impossible to find a tiny sharp minima among the loss landscape. 


4. Lottery ticket hypothesis: 
The initialization lottery can bring good initial settings for efficient (i.e. "winning tickets") sub-networks to be selected by the optimization process.  The overparametrization allows for a lot of tickets to be tried and good generalization capabilities requires only a few winning subnets to arise. 
In other words, the higher the bigger the network the more lottery tickets you have. 
From this, we can consider that 



References:
- Zhang, Chiyuan, et al. "Understanding deep learning requires rethinking generalization." _arXiv_, 2016, https://doi.org/10.48550/arXiv.1611.03530.
- Arpit, Devansh, et al. "A Closer Look at Memorization in Deep Networks." _arXiv_, 2017, https://doi.org/10.48550/arXiv.1706.05394.
- Belkin, Mikhail, et al. "Reconciling modern machine learning practice and the bias-variance trade-off." _arXiv_, 2018, https://doi.org/10.1073/pnas.1903070116.
- Dinh, Laurent, et al. "Sharp Minima Can Generalize For Deep Nets." _arXiv_, 2017, https://doi.org/10.48550/arXiv.1703.04933.
- Huang, W., et al. "Understanding Generalization through Visualizations." _arXiv_, 2019, https://doi.org/10.48550/arXiv.1906.03291.
- Frankle, Jonathan, and Carbin, Michael. "The Lottery Ticket Hypothesis: Finding Sparse, Trainable Neural Networks." _arXiv_, 2018, https://doi.org/10.48550/arXiv.1803.03635.


Potentially interesting (found but not-read) papers on the problem: 
- Neyshabur, Behnam, et al. "In Search of the Real Inductive Bias: On the Role of Implicit Regularization in Deep Learning." _arXiv_, 2014, https://doi.org/10.48550/arXiv.1412.6614.
- Neyshabur, Behnam, et al. "Norm-Based Capacity Control in Neural Networks." _arXiv_, 2015, https://doi.org/10.48550/arXiv.1503.00036.
- Nagarajan, Vaishnavh, and Kolter, J.. "Uniform convergence may be unable to explain generalization in deep learning." _arXiv_, 2019, https://doi.org/10.48550/arXiv.1902.04742.
- Kawaguchi, Kenji, et al. "Generalization in Deep Learning." _arXiv_, 2017, https://doi.org/10.48550/arXiv.1710.05468.
- Belkin, Mikhail, et al. "Reconciling modern machine learning practice and the bias-variance trade-off." _arXiv_, 2018, https://doi.org/10.1073/pnas.1903070116.
- Wei, Alexander, et al. "More Than a Toy: Random Matrix Models Predict How Real-World Neural Representations Generalize." _arXiv_, 2022, https://doi.org/10.48550/arXiv.2203.06176.
- Chatterjee, Satrajit, and Zielinski, Piotr. "On the Generalization Mystery in Deep Learning." _arXiv_, 2022, https://doi.org/10.48550/arXiv.2203.10036.
- Goldblum, Micah, et al. "Truth or Backpropaganda? An Empirical Investigation of Deep Learning Theory." _arXiv_, 2019, https://doi.org/10.48550/arXiv.1910.00359.
- Louis, Ard. "Generalization bounds for deep learning." _arXiv_, 2020, https://doi.org/10.48550/arXiv.2012.04115.
- Maddox, Wesley, et al. "Rethinking Parameter Counting in Deep Models: Effective Dimensionality Revisited." _arXiv_, 2020, https://doi.org/10.48550/arXiv.2003.02139.

