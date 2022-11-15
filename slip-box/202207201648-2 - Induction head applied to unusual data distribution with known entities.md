Previous: [[202207201648 - Data novelty and distribution as dimensions of in-context learning]]
Source: [[]]
Consider: [[]]
Tags: 
______________

How does induction heads apply to such kind of situation? 
It seems that they do apply: [[A Mathematical Framework for Transformer Circuits]] claims that induction heads are the basic block of in-context learning.

`[e][pn][pm]...[e'][pn'] -> [pm']`

```
[e_1][pn_1][pm_1][eos]
[e_2][pn_2][pm_2][eos]
[e_3][pn_3] -> [pm_3]
 ```

This situation relies both on a "two layer model induction head" and on learning to map tokens to concepts.
- Learning the concepts produces a consistent mapping between tokens: `[a][b][c] <-> [a'][b'][c'] <-> [a''][b''][c'']`
- The induction head perform the copy of the next token based on previous utterance :
`[a][b][c]...[a'][b'] -> [c']`

```python
def QK_circuit(tokens, target):
	for i, token in enumerate(tokens):
		if token == target:
			return i, token
	return 0, -1

def inference(tokens):
	sentence = get_sentence(tokens)
	curr_entity = get_entity(sentence)

	pos, token = QK_circuit(tokens[:-1], tokens[-1])
	if pos == 0:
		return None
	else:
		return concept_mapping(tokens[pos+1], curr_entity)
```