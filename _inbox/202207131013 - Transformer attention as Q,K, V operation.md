Previous: [[]]
Source: [[Transformers from scratch]]
Consider: [[]]
Tags: #attention #transformer #table_lookup
______________

Does attention need that much operations to be expressed? 

$$\text{Attention}(Q,K,V) = \text{softmax}(\frac{QK^T}{\sqrt{d_k}})V$$

Would it not be possible to use only one matrix instead of $Q, K$ ?

$$\text{Attention}(Q,K,V) = \text{softmax}(\frac{A}{\sqrt{d_k}})V$$
