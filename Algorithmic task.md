## The task
Given a sequence representing: 
1. a list
2. an update of one element of the list using an index 
3. an updated list
classify wether the updated list is the expected one.
```
# Example 1: accurately updated list
V1;V2;V3-IDX1:V4-V1;V4;V3
            ^  ^     ^

# Example 2: Inaccurately updated list: wrong value
V1;V2;V3-IDX1:V5-V1;V4;V3
            ^  ^     ^
```

## Hypothesis

An hand-coded version of the algorithm for this task would look like this:

```
# Step 1.1: collect the idx of the updated value [Layer 1]
<END>: 
- Positional query: what is the value stored at pos <IDX> (i.e. n tokens before me)?
# The model was trained with always the same list dims, therefore it just requires to know where to look at (shifted identity matrix)
- Key (<IDX>): I'm 8 tokens before
- Value (<IDX>): My value is #IDX

OR 
<VX>: 
- Positional query: is the value stored at pos <IDX> (i.e. n tokens before me) my pos? (i.e. Am I at the updated position?)
- Key (<IDX>): I'm n tokens before AND corresponding to your pos
- Value (<IDX>): You are updated


# Step 1.2: collect the updated value [Layer 1]
<END>:
- Positional query: what are the values stored 6 tokens before me? (i.e <V4>)
# Same as above
- Key (<V4>): I'm 6 tokens before
- Value (<V4>): My value is #V4

OR 
<VX>: 
- Positional query: is the value stored at <V4> (i.e. n tokens before me) my value? (i.e. Have I the proper value?)
- Key (<V4>): I'm 6 tokens before AND having value <V4> 
- Value (<V4>): You are updated with the proper value


# Step 2: collect the value having this idx in the updated list [Layer 2]
<END>: 
- Positional query: what is the value stored at pos #IDX in the updated list AND equal to #V4
- Key (<VX>): I'm at <VX> and equal to #V4
- Value (<VX>): I'm equal to #V4

OR
<END>: 
- Positional query: what is the value stored at pos #IDX in the updated list AND properly updated
- Key (<VX>): I'm at <VX> and properly updated
- Value (<VX>): I'm equal to #V4


# Step 3: compare whether the value in the updated list and the expected one are the same
Output True: I'm equal to #V4 * a positive vector
Output False: I'm equal to #V4 * a negative vector
```

