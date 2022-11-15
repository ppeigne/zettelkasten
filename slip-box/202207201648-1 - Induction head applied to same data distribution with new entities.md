Previous: [[202207201648 - Data novelty and distribution as dimensions of in-context learning]]
Source: [[]]
Consider: [[A Mathematical Framework for Transformer Circuits]]
Tags: #induction_head 
______________

In the case of [[Data Distributional Properties Drive Emergent In-Context Learning in Transformers]] (i.e. same distribution of data but novel unknown entities), it seems that induction heads are perfectly well suited to address the problem (if the model displays at least two attention layers). The solution to this task consist in finding the previous occurrence of the token using a K-composition based attention-head.

*'The minimal way to create an induction head is to use K-composition with a previous token head to shift the key vector forward one token'* ([[A Mathematical Framework for Transformer Circuits]])

We are typically in a situation described in [[A Mathematical Framework for Transformer Circuits]] as *"Two layer model induction head"*:
`[a][b] ... [a] → [b]`: `[ Pot][ters] ... [ Pot] → [ters]`

```python
def QK_circuit(tokens, target):
	for i, token in enumerate(tokens):
		if token == target:
			return i, token
	return 0, -1


def inference(tokens):
	pos, token = QK_circuit(tokens[:-1], tokens[-1])
	if pos == 0:
		return None
	else:
		return tokens[pos+1]
```
