Previous: [[202207261259 - Induction heads and Set synthetic task]]
Source: [[]]
Consider: [[Transformer circuits]]
Tags: #synthetic_dataset  #induction_head #set_operation
______________
A first approach should be rule/procedure such as:
	Check if the token already appeared. 
	- If it did, write nothing. 
	- Else, write the token.

According to the theory, 
The QK circuit should attend to a previous utterance of the token:
	-if  `<token>`: the OV circuit should erase it (add negative value)
	- if `<start>`: the OV circuit should write it down

#FIXME: confirm this statement

A not efficient, but close to what the attention operations are supposed to do, python implementation:
```python
def set_operation(tokens: List[int]) -> List[int]:
	result = []
	for i, token in enumerate(tokens):
		duplicate = False
		for j in range(i):
			if tokens[j] == token:
				duplicate = True
				break
				
		if not duplicate:
			result.append(token)
	
	return t
```

```python
def QK_circuit(tokens, target):
	for token in tokens:
		if token == target:
			return token
	return -1

def set_operation(tokens):
	results = []
	for i, token in enumerate(tokens):
		QK_res = QK_circuit(tokens[:i], token)
		if QK_res == -1:
			results.append(token)
	return results
```
