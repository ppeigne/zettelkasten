Source: https://www.alignmentforum.org/s/EmDuGeRw749sD3GKd/p/NXqs4nYXaq8q6dTTx
Consider: [[]]
Tags: #hch #recursive_behavior #ida #amplification 
______________

A recursive structure.
Human $H$ as access to question-answering system $Q$. 
$Q$ acts as if $H$ consults $Q$ to answer the question.
$$
\begin{array}{ll}
H \rightarrow_\text{consults} & Q & \\
& H' \rightarrow_\text{consults} & Q & \\
& & H' \rightarrow_\text{consults} & Q & \\
& & & H' \rightarrow_\text{consults} \dots
\end{array}
$$

This is the ultimate amplification process (if you keep the process linear, i.e. not as a tree structure).

The algorithm $A$ predicts the output of $HCH^A$ (i.e. of what human $H$ would output after consulting $HCH^A$).
$A$ is not an $HCH$ by itself but *predicts* the output of an $HCH$ for a given task.
However, $HCH^A$ *IS* the result of $A$ predicting the output of $HCH^A$.

$$
\begin{array}{ll}
HCH^P(x) & = & P(HCH^P(x))\\
& & P(P(HCH^P(x)) & = & P(P(P(HCH^P(x)))\\

\end{array}
$$
