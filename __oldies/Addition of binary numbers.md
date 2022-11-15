# Addition of binary numbers

In order to add two binary numbers we must build a logical circuit allowing the following results: 
- 0 + 0 = 0
- 1 + 0 = 1
- 0 + 1 = 1
- 1 + 1 = 10

### Half adder

To get the last result (1 + 1 = 10) we must carry ouput. In other word, the truth table of our operation is the following : 

| a | b | carry | sum |
|:-:|:-:|:-:|:-:|
|0|0|0|0|
|1|0|0|1|
|0|1|0|1|
|1|1|1|0|

The sum column correspond to a [[XOR gate]] and the carry column to an [[AND gate]].

Corresponding logic gate circuit is called a *half adder*. 

![half adder circuit](http://www.c-jump.com/CIS77/images/add_ab.gif)

### Full Adder
There is a strong limitation to *half adder* circuits: they cannot handle a carry over from previous bit. 

To fix this situation, it is necessary to use three inputs instead of two and to chain two half adder: 
- the first provide the carry output and sum of the given numbers
- the second add the results of the first one to the carry in input to handle possible carry over. 

![full adder](http://www.c-jump.com/CIS77/images/full_adder.gif)

The full adder has the following truth table:

| a | b | carry in| # |carry out | sum |
|:-:|:-:|:-:|:-:|:-:|:-:|
|0|0|0|#|0|0|
|0|0|1|#|0|1|
|0|1|0|#|0|1|
|0|1|1|#|1|0|
|1|0|0|#|0|1|
|1|0|1|#|1|0|
|1|1|0|#|1|0|
|1|1|1|#|1|1|


##### Remarks
The use of a final [[OR  gate]] can be surprising at the end of the calculation of the carry output. What if both [[AND gate | AND gates]] outputs 1? 
It is an impossible case: 
- If the leftmost [[AND gate]] is 1, then the result of the leftmost [[XOR gate]] must be 0 (they have the same intputs). 
- Then the second [[AND gate]] cannot be 1 because one of its inputs is the output of the first [[XOR gate]] (which is zero). 