## The task
Given a sequence representing: 
1. a list
2. an update of one element of the list using an index 
3. an updated list
classify wether the updated list is the expected one.
```
# Example 1: Acurately updated list
V1;V2;V3-IDX1:V4-V1;V4;V3

# Example 2: Inaccurately updated list
V1;V2;V3-IDX0:V4-V1;V4;V3
```

## Hypothesis

An hand-coded version of the algorithm for this task would look like this:

```
# Step 1.1: collect the idx of the updated value [Layer 1/2]
<END>: 
- Positional querry: what is the value stored 8 tokens before me? (i.e <IDX>)
# The model was trained with always the same list dims, therefore it just requires to know where to look at (shifted identity matrix)
- Key (<IDX>): I'm 8 tokens before
- Value (<IDX>): My value is #IDX

# Step 1.2: collect the updated value [Layer 1/2]
<END>:
- Positional querry: what are the values stored 6 tokens before me? (i.e <V4>)
# Same as above
- Key (<V4>): I'm 6 tokens before
- Value (<V4>): My value is #V4


# Step 2: collect the value having this idx in the updated list [Layer 2]
<END>: 
- Positional querry: what is the value stored at pos #IDX in the updated list? (i.e. <VX>)
- Key (<VX>): I'm at <VX>
- Value (<VX>): My value is #VX

# Step 3: compare whether the value in the updated list and the expected one are the same
Ideally a NAND-like operation over the content of <END> (performed by the Unembedding Matrix) but it is not possible to perform a NAND with a 1-layer MLP. 
However we have 2 outputs and not only one, which makes it much easier to perform.

Output
- True update: multiply by a vector of -n and add a bias of 2*n. If more than 1 elements, the result will be bellow 0, else above n. 
- Wrong update: multiply by a vector of n and add a bias of -n. If more than 1 elements, the result will be above n, else bellow 0. 
```

$$
WU = \
$$