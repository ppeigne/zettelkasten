# [Feature visualisation (Olah et al, 2017)](https://distill.pub/2017/feature-visualization/)

## Feature visualization by Optimization
Start from random noise and optimize the input until it activates the neurons firing.

### Objectives :
Neuron, Channel, Layer, Class logits (more useful for visual interpretation), Class proba (less usefull because increasing softmax usually implies reducing the alternative and not improving the likelihood of the target task).

![[Screenshot from 2022-03-09 07-58-26.png]]

### Why visualize by optimization ?
Viz. gives better understanding of what the model is really looking for, while looking at the input examples activating the model we could not always understand the features the model looks for.


### Achieving diversity through optimization

#### Diversity objective
Adding a diversity objective to generate diverse examples of activation can gives better understanding of what the triggering features really are.

![[Screenshot from 2022-03-09 08-15-28.png]]

Limitations: 
- can mix-up the class of triggering examples.
- some very different class of object (like cat, fox and  car) could be looked for by a single neuron. The optimization with diversity will not generate examples of each class but mixed class images instead.

![[Screenshot from 2022-03-11 08-54-10.png]]

*"Examples like these suggest that neurons are not necessarily the right semantic units for understanding neural nets."*

## Interaction between neurons
Activation space: the space of all possibles combinations of neurons activations.
Basis vector: individual neuron activations from the activation space

*"Random directions often seem interpretable, but at a lower rate than basis directions."*

Arithmetic on neurons can be done like in word embedding.
*"if we add a “black and white” neuron to a “mosaic” neuron, we obtain a black and white version of the mosaic. This is reminiscent of semantic arithmetic of word embeddings as seen in Word2Vec or generative models’ latent spaces."*

![[Screenshot from 2022-03-11 09-00-21.png]]

Linear interpolation (FIXME) can be done between two neurons activations to get a gradient (spectrum) between them. *"This is similar to interpolating in the latent space of generative models."*

![[Screenshot from 2022-03-11 09-05-15.png]]

Limitations: 
How to select the most meaningful direction is still (and even if they exists)
How the directions interact (interpolation shows only a tiny subset)


## The Enemy of Feature Visualization
Optimization without any kind of constraint makes high-frequency pattern arising. It seems to be somewhat related to adversarial examples.

### The spectrum of regularization

#### Frequency penalization
Directly **target the high-frequency noise.** 
- Penalize variance between neighboring pixels
- Blurring 
Limits: reduce legitimate high-frequency features like edges. (Blurring could be replaced by bilateral filter to preserve edges)


#### Transformation robustness
Stochastically jitter, rotate or scale the image before applying optimization to **find examples that still activate the optimization target even if slightly transformed.**


#### Learned prior
Learn a model of the real data and try to enforce that.
Limits: what came from the model being visualized and what came from the prior ?

## Preconditioning and  Parametrization
Preconditioning: directly regularizing the gradient

*"You can think of it as doing steepest descent to optimize the same objective, but in another parameterization of the space or under a different notion of distance.  Gradient blurring is equivalent to gradient descent in a different parameterization of image space, where high frequency dimensions are stretched to make moving in those directions slower. Gradient Laplacian Pyramid normalization is a kind of adaptive learning rate approach in the same space."*

*"**This changes which direction of descent will be steepest, and how fast the optimization moves in each direction, but it does not change what the minimums are**. If there are many local minima, it can stretch and shrink their basins of attraction, changing which ones the optimization process falls into."*