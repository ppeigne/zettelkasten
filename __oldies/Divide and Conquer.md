Source : https://skerritt.blog/divide-and-conquer-algorithms/

### Recursion
Fibonacci : 
```python
def F(n):
	if n == 0 or n == 1:
		return n
	else:
		return F(n-1) + F(n-2)
```


### Divide & Conquer
1. Divide
	If the problem is small enough solve it. Else divide it into sub-problems.
2. Conquer
	Solve the problem recursively. 
3. Combine
	Merge the sub-problems into a solution to the original problem.

```python
def recur_factorial(n):
	if n == 1:
		return n
	else:
		return n * recur_factorial(n-1)
```

$$ OPT(i) = \begin{cases} 0, \quad \text{If i = 0} \\ max{v_i + OPT(next[i]), OPT(i+1)},  \quad \text{if n > 1} \end{cases}\end{cases} $$