# Iterated distillation amplification 
Pseudo code:
```python
def ida_solver(problem):
	if is_simple_enough(problem):
		return solve(problem)

	else:
		return ida_solver(concat_sub_problems(divide_problems(problem)))
```

### Summarizing books 
solve = summarize 1 chunk of text
is_simple_enough = text chunk is smaller than a certain amount of characters
divide_problems = divide text into smaller chunks

### QA answering
solve = answer one question from a corpus **using X**
is_simple_enough = 