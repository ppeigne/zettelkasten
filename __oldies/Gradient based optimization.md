# Gradient based optimization

Gradient based optimization is a type of optimization method using the [[gradient]] of a model's [[cost function]] to perform an update of its [[parameters]].  It is the canonical approach currently used in [[deep learning]] to [[training | train]] [[neural network | neural networks]]. 

### Principles: 
Given a model M having parameters p, X, y : 
for i in range iter : 
predictions = M.forward(X)
errors = cost(predictions, y)
gradient = M.backward(X, error)
M.p := M.p - alpha * gradient

### Gradient based optimizers:
- [[Gradient descent]]
- [[Stochastic gradient descent]]
- [[Momentum]]
- [[Nesterov Momentum]]
- [[Adagrad]]
- [[AdaDelta]]
- [[Adam]]
- [[NAdam]]