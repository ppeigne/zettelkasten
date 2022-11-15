Source: https://arxiv.org/abs/2111.02080
Consider: [[]]
Tags: #in-context_learning #synthetic_dataset 
______________

# Claim
In-context learning can emerge from data having "long-range coherence". Such data can be synthesized using mixture of HMMs. 

Small synthetic dataset can produce in-context learning in **both LSTMs and Transformers**


# Key takeaways

### The Synthetic Dataset
#### Concepts, entities, properties
5 concepts are generated. Concepts correspond to a transition matrix between ten entities and ten properties. The transition between entities is override to make sure it is slow. One property represents the end of the sentence (same token for all entities).

Tokens are created combining letters to reach the vocabulary size. E.g: a->z, aa->az, etc. 

The token are uniformly sampled from the vocabulary to populate the concept matrices. Given the small size of the vocabulary (50, 100, or 150) compared to the total of entries (450) (90 for each 'concept matrix' (9x10) times 5 concepts), the token are assumed to be present in more than one situation (#FIXME : confirm that).

#### Text generation
##### Training
Each training sample is produced using one concept matrix (uniformly sampled from the concept set)

##### Prompt
Each prompt example is produced using one concept matrix. From that matrix, a forced starting point is used and a string of a determined size is produced. The sequence of properties is then reused to produce other example of the same 'latent concept' for other entities.