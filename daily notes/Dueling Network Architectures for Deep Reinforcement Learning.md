Source: https://arxiv.org/abs/1511.06581
Consider: [[]]
Tags: 
______________

The point is to learn to evaluates the given states and the possibles actions separately, using two separated streams ($V_\beta$ and $A_\alpha$) plugged at the end of $Q_\theta$.
$$Q(\phi, a; \theta, \alpha, \beta) \approx V(\phi; \theta, \beta ) + A(\phi, a; \theta, \alpha )$$

More precisely 
$$Q(\phi, a; \theta, \gamma, \beta) = V(\phi; \theta, \beta ) + \bigg(A(\phi, a; \theta, \gamma) - \frac{1}{|\mathcal{A}|} \sum_{a'} A(\phi_j, a_{j}'; \theta, \alpha)\bigg)$$

This modifications let $V_\beta$ (the evaluation of the current state $\phi_j$) be updated without being mapped to a specific action $a_j$.

Before:
$\theta$ is updated only for the specific combination of state $\phi_j$ and action $a_j$. 

$$
\begin{array}{ll}
\theta & \leftarrow & \theta - \gamma \nabla L(y_j, \hat{y}_j) & \\
\theta & \leftarrow & \theta - \gamma \nabla L(y_j, Q(\phi_j, a_j ; \theta)) & \\
\theta & \leftarrow & \cancel{\theta - \gamma \nabla L(y_j, Q(\phi_j, a' ; \theta))} & \forall a' \in \mathcal{A} \neq a_j
\end{array}
$$

After:
- $\beta$ is updated only based on the state $\phi_j$(i.e. is updated for any action).
$$
\begin{array}{ll}
\beta & \leftarrow & \theta - \gamma \nabla L(y_j, V(\phi_j; \theta, \beta)) & \\
\beta & \leftarrow & \theta - \gamma \nabla L(y_j, V(\phi_j, a; \theta, \beta)) & \forall a \in \mathcal{A} \\
\end{array}
$$

-  $\alpha$ is updated based on the action $a_j$ given the state $\phi_j$.
$$
\begin{array}{ll}
\alpha & \leftarrow & \theta - \gamma \nabla L(y_j, A(\phi_j, a_j; \theta, \alpha)) & &
\end{array}
$$