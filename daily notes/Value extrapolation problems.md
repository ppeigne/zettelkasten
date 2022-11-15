*Assume you have access to two labeled image sets of equal size, $H$ and $L$ (which you could consider as showing pictures of huskies and lions, but that isn't important). You also have access to a large unlabelled image dataset, $U$. Let $C_0,C_1,C_2$, etc... be classifiers that distinguish $H$ from $L$, giving each image a score between 0 ($H$) and 1 ($L$). They need not be perfect, but they are all better than chance.*

## Problem 1
*Given classifiers $C_0,C_1,\dots,C_{n−1}$, how would you define a classifier $C_n$ that correctly classifies $H$ and $L$, but is "independent" of the other $C_i$; i.e. uses different features to do its classification. 
You can do this in some intrinsic way, or relative to the set $U$ . 
We're interested in how you choose to formalize the concept of independence, of what "using different features" means (note that you don't have access to a list of features, so if you need them explicitly, you'll need to explain how you get them). (We are interested in what you come up with; there is not necessarily a canonical solution to this problem).*

### Answer
The approach used by Lee et al. (2022) seems pertinent to define our problem. According to their definition, a classifier $C_n$ could be defined as "independent"  from another classifier $C_i$ if they output *"predictions that are close to being statistically independent from each other"*. 

The idea is that if the model have very low statistical independence (or mutual information) on unseen (and probably under-specified) data, they probably rely on different features to perform classification. The data is almost always under-defined (several hypothesis can fit the data) because real data is more complex than the task it is trained for:  is your lion classifier a savanna detector or a lion's one? Is your husky detector a husky detector or a blue eyes detector ? A low mutual information is a good proxy for different hypothesis being learned. 

The mutual information can then be measured using the KL divergence between each pair of prediction $\hat y_n, \hat y_i$ made by classifiers $C_n$ and $C_i$ over unseen data given the following formula:
$$
\begin{array}{ll}
L_{MI}(C_n, C_i) &= &D_{KL}(p(\hat y_n, \hat y_i) || p(\hat y_n) \otimes p(\hat y_i)) \\
&= & p(\hat y_n, \hat y_i) \cdot \log(p(\hat y_n) \otimes p(\hat y_i))) - p(\hat y_n, \hat y_i) \cdot \log(p(\hat y_n, \hat y_i))\\
&=& p(\hat y_n, \hat y_i) \cdot [\log(p(\hat y_n) \otimes p(\hat y_i))) - \log(p(\hat y_n, \hat y_i))]
\end{array}
$$
where $\hat y_i = C_i(x)$ and $x \in U$.

The lower the score the more independent the distributions. The more independent the distributions, the more independent the classifiers.

Intuitive explanation:
The KL divergence implies that both terms are multiplied by the joined probability of the two distributions. If those distributions are not correlated, their joined probability distribution $P(x,y) = P(x) * P(y)$ will be low.   


## Problem 2
*Same as for problem 1, but now imagine you’ve got $C_0,\dots,C_{n−1}$    
as black box classifiers, and you want to actually construct $C_n$ using a neural net. 
What loss function can you use to capture your previous definition of ”independence”? Can you make it differential? Can it be trained by gradient descent given batches of images from $H$, $L$ and $U$? 
If $C_0,\dots,C_{n−1}$ were not black boxes, would this make any difference?*

### Answer
We can tweak the strategy from Lee et al. (2022). 
The main difference is that in their settings, all the classifiers are different heads plugged on the same backbone network, while in our setting the other classifiers are not defined like that. However, this difference should not impede to reuse their strategy. 

The point is to train a new classifier under the constraint of minimizing its mutual information with every other already trained models when evaluated on unseen data. (The mutual information should be high on training data because the models are all trained to predict the same labels, therefore the mutual information should be evaluated on samples from $U$). 

The loss (inspired by Lee et al. (2022)) have the following formula:
$$
\mathscr{L}_{\text{xent}}(C_n) + \lambda_1\sum_{i < n} \mathscr{L}_{\text{MI}}(C_n, C_i)
$$
The settings difference implies that we are only training $C_n$ instead of training each classifier at once. Therefore, the loss function only evaluates the cross-entropy loss of $C_n$ and the mutual information of $C_n$ with every other classifiers.

This loss is differentiable and the model can be trained by gradient descent using it. The only drawback comes from the fact that the model has to compute the unlabeled samples from U as well, generating a 2x slowdown.

If the previous classifiers are not black boxes we can also add monitoring tools such as gradcam to look at the features used by the model and potentially penalize the new classifier if it start to have results too close to previous classifiers.


## Problem 3
*List three published or arXiv papers that you think are relevant to the previous problem or to concept extrapolation.*

### Answer
Lee, Yoonho, et al. "Diversify and Disambiguate: Learning From Underspecified Data." _arXiv_, 2022, https://doi.org/10.48550/arXiv.2202.03418.

Jeon, Hong, et al. "Reward-rational (implicit) choice: A unifying formalism for reward learning." _arXiv_, 2020, https://doi.org/10.48550/arXiv.2002.04833.

