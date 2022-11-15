Source: https://transformer-circuits.pub/2022/in-context-learning-and-induction-heads/index.html
Consider: [[A Mathematical Framework for Transformer Circuits]]
Tags: #induction_head #transformer 
______________

# Claim

# Key takeaways
### In-context learning
##### Definition
In-context learning is defined simply as, for a model, having later tokens easier to predict than the first ones because of information obtained from context (i.e. the previous part of the prompt). The longer the context the better the prediction.

*"In modern language models, tokens later in the context are easier to predict than tokens earlier in the context. [...] as the ability to predict later tokens from earlier ones gets better, it can increasingly be used in interesting ways (such as specifying tasks, giving instructions, or asking the model to match a pattern) that suggest it can usefully be thought of as a phenomenon of its own."*

- Micro-perspective (task specific): few-shot learning
- Macro-perspective (task agnostic): observing the loss at different token indices

