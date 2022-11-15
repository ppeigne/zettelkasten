Source: 
Consider: [[]]
Tags: 
______________

Problem:
$\varepsilon$-greedy strategy are not efficient #FIXME: why ?




Solution:
The learned perturbation of the network weights drive the exploration.

Key insight
**"A single change to the weight vector can induce a consistent and potentially very complex state-dependent change in policy over multiple time steps"**

$$
\begin{array}{ll}
y = W & X & + & b \\
y = \underbrace{(\mu^{(W)} + \sigma^{(W)} \odot \varepsilon^{(W)})}_W & X & + &\underbrace{(\mu^{(b)}+ \sigma^{(b)} \odot \varepsilon^{(b)})}_b\\
\\
\text{where }\\ 
\mu^{(W)} \in \mathbb{R}^{q \times p} &&\text{and}& \sigma^{(W)} \in \mathbb{R}^{q \times p}\\
\mu^{(b)} \in \mathbb{R}^{q} &&\text{and}& \sigma^{(b)} \in \mathbb{R}^{q}\\

\varepsilon^{(W)} \in \mathbb{R}^{q \times p} &&\text{and}& \varepsilon^{(b)} \in \mathbb{R}^{q}\\

\varepsilon_{i,j}^{(W)} = f(\varepsilon_i)f(\varepsilon_j)\\
\varepsilon_{i,j}^{(b)} = f(\varepsilon_j)\\
f(x) = \text{sign}(x) \sqrt{|x|}
\end{array}
$$

Scenario no noise required:
$$
\begin{array}{ll}
& \sigma = 0 \\
y = \underbrace{(\mu^{(W)} + \cancel{\sigma^{(W)} \odot \varepsilon^{(W)})}}_W & X & + &\underbrace{(\mu^{(b)}+ \cancel{ \sigma^{(b)} \odot \varepsilon^{(b)})}}_b\\
y = \mu^{(W)} & X & + &\mu^{(b)}\\
\\
& \sigma = 0 \rightarrow\mu^{(W)} = W \\ 
& \sigma = 0 \rightarrow\mu^{(b)} = b 

\end{array}
$$

