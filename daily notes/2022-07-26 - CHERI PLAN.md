## Key takeaways



## The context
### The transformer architecture

### In-context learning

### Induction heads and mechanistic interpretation of transformers
- OV circuit
- QK circuits
- Induction heads

### Norm growth and saturation
Saturation brings two kind of behaviors

## The problem(s)
### Definitions of in-context learning
In-context learning is not well defined and should be.
[[202207201648 - Data novelty and distribution as dimensions of in-context learning]]

### Induction heads theory tested only on natural language data
The theory should be tested on synthetic tasks. #FIXME *Check what kind of test were done in the Induction heads paper.*

### Induction heads theory tested only on token-prediction task (not in-context learning) 
#FIXME *Check whether it is true in the Induction heads paper*

### Induction heads required for in-context learning
- Claim that RNNs can perform in-context learning as well 

### Relation between the saturation (norm growth) hypothesis and the induction heads theory 
Saturation is supposed to bring two kind of behavior (argmax and average). This claim is different from the way induction heads are supposed to work. #FIXME *Check if it is the case in  the Induction heads paper.*

### Norm growth and other metrics
How do compare the norm growth with other metrics used by anthropic (eigen values)?


## The hypotheses
### 1. Interactional hypothesis 
What does the induction heads theory says about the in-context learning task types? Does the experience confirm such statements? 

#### Induction heads vs 'knowledge-based' in-context learning
Induction heads should be present in 'knowledge-based' in-context learning
[[202207201648-1 - Induction head applied to same data distribution with new entities]]

#### Induction heads vs 'distributional' in-context learning
[[202207201648-2 - Induction head applied to unusual data distribution with known entities]]

#### Induction heads vs 'knowledge-based' AND 'distributional' in-context learning

### 2. Monitoring and prediction of in-context learning
Is it possible to predict the arising of in-context learning abilities while only looking at the metrics?


## The experiment(s)

### 1. 

#### Description of the experiment
#### Expected outcomes of the experiment
#### Conclusions drawn from this outcomes


#######################
Experiment: built properties/entities with multiple tokens. e.g `[ Pot][ters]`