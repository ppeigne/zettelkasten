# Zoom In: An introduction to Circuits

Zooming in the neural nets brings meaningful insight about the internal machinery of NNs. 
"Circuit" of connections reveal internal logic (even internal algorithms!).

### 1. Features
> Features are the fundamental unit of neural networks. They correspond to directions. They can be rigorously studied and understood.

Arguments (based on "curves detectors"): 
1. Feature visualization: optimization results generate curves to activate these neurons
2. Dataset examples: the examples are curve-shaped objects
3. Synthetic examples: designing images containing synthetic curves triggers theses neurons
4. Joint tuning: rotating an image progressively change the activation of the neurons from a specific position neurons into another specific position neuron
5. Feature implementation: we can read a curve detection algorithm off of the weights
6. Feature use: these neurons are used for detecting objects involving curves farther into the NN
7. Handwritten circuits: it is possible to handcraft working curve detection algorithm which mimic the original curve detection neurons 

#### Polysemantic neurons
A lot of neurons responds to multiple unrelated inputs (eg. cat face, front of cars and car legs)
- Resolving by "unfolding"
- Training to not exhibit polysemanticity in the first place

Disentangling representations

Possible source : "superposition"

### 2. Circuits
>  Features are connected by weights, forming circuits.  
These circuits can also be rigorously studied and understood.

The weights connecting an earlier detector to a later one are often visually meaningful.

![[Screenshot from 2022-03-12 09-50-49.png]]

- Equivariance: symmetry of the problem is reflected as a symmetry in the weight. I.e the weights rotates with the orientation of the curve detector
- Unioning over cases: detects two cases and then takes a union over them to create invariant "multifaceted" units.
- Superposition: after building a pure one-class detection units, the features are spread over a number of other neurons primarily seeming doing something else.

#### Circuit motifs
Recurring pattern in complex graphs. 

### 3. Universality
> Analogous features and circuits form across models and tasks.

The evidence is only anecdotal for now, but same features detectors can be found among a lot of CV models. 

### Interpretability as a Natural Science
Rigorous empirical investigation of tiny subgraphs of a NN are tractable and falsifiable.

Statements are only about circuits and not whole models, but "with sufficient effort, statements about model behavior could be broken down into statements about circuits. If so perhaps circuits could act as a kind of epistemic foundation for interpretability "