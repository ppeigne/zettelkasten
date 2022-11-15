On its most basic level, in-context learning is defined (for a model being given a text prompt as input) as the property of being able to produce better prediction for the later tokens of the prompt than for the earlier ones. This improvement is a result of the model being able to use the information present in the prompt (also called the context), i.e. "to learn from context".

However, starting from this definition it is possible to produce different interpretations of what "learning from context" means. Those orthogonal interpretations relies on a different approach of how to bring novelty into the context:
- Novelty of the entities: the context's entities are unknown to the model as being never encountered in the pre-training phase.
- Novelty of the tokens distribution: the model is given an unusual task based on an unusual distribution of tokens.  


Those different approaches then usually produce theoretical claims about the  

relies essentially on orthogonal dimensions 

*"In modern language models, tokens later in the context are easier to predict than tokens earlier in the context. [...] as the ability to predict later tokens from earlier ones gets better, it can increasingly be used in interesting ways (such as specifying tasks, giving instructions, or asking the model to match a pattern) that suggest it can usefully be thought of as a phenomenon of its own."*

- Micro-perspective (task specific): few-shot learning
- Macro-perspective (task agnostic): observing the loss at different token indices
