Source: 
Consider: [[]]
Tags: 
______________

Parameterized Q function : $Q_\theta(s, a)$

Learning rule:
$$
\text{target}(s')= R(s,a,s') + \gamma \max_{a'} Q_\theta(s', a')
$$

Update:
$$
\theta_{k+1} = \theta_k -\alpha \nabla_\theta [\frac{1}{2}(Q_\theta(s,a)-\text{target}(s'))^2]|_{\theta=\theta_k}
$$

$$
\theta_{k+1} = \theta_k - \alpha \nabla_\theta [\frac{1}{2}(Q_\theta(s,a)-(R(s,a,s') + \gamma \max_{a'} Q_\theta(s', a')))^2]|_{\theta=\theta_k}
$$