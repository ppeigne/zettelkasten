Attractors are fixed point in the space of value (i.e. string outputs) toward which, given a specific seed value (i.e. prompt), the (deterministic?) function (i.e. model) output converges. 

### Observing attractors
#### Without access to the model internals
Using a sentence embedding, compare whether specific prompts converges toward the same basin of attraction. 

#### With access to the model internals
- Observe the cosine sim between `<END>` embedding for every forbidden behavior when triggered and not triggered
- Train a probe to detect where the instructions are encoded into `<END>`
- Patching (eg patch a specific word with a forbidden one -> "tell me a joke about women" vs "tell me a joke about pandas")