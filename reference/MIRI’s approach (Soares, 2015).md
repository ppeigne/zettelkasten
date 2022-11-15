# [MIRI’s approach (Soares, 2015)](https://intelligence.org/2015/07/27/miris-approach/)

## Specializing assumptions
1. **We focus on scenarios where smarter-than-human machine intelligence is first created in _de novo_ software systems (as opposed to, say, brain emulations).**


2. **We specialize almost entirely in technical research.**

Selecting project using the following question:
_What would we still be unable to solve, even if the challenge were far simpler?_

E.g. : we might study AI alignment problems that we could not solve even if we had lots of computing power and very simple goals.

Problems should then be:
1. tractable: we can do mathematical research on them today
2. uncrowded: not likely to be addressed during normal capabilities research 
3. critical: could not safely delegated to a machine unless the problem is solved in a first place


The claim:
*" The controversial claim here is that the above question — “what would we be unable to solve, even if the challenge were simpler?” — is a generator of open technical problems for which solutions will help us design safer and more reliable AI software in the future, regardless of their architecture."*

Types of problems:
*"There are two types of open problem in AI. One is figuring how to solve in practice problems that we know how to solve in principle. The other is figuring out how to solve in principle problems that we don’t even know how to brute force yet."*

We must first solve in principle (making us able to brute force a solution) and then we can solve in practice.


Arguments in favor of the claim:
1. Creating a powerful AI system without understanding why it work is dangerous
2. We could not yet create a beneficial AI system even via brute force
3. Figuring out how to solve a problem in principle yields many benefits
4. This is an approach researchers have used successfully in the past


1. 

Trial an error should be avoided while designing superintelligent agents.
We cannot anticipate every instances of wrong behavior that is why we must "have a solid understanding of how the search process works and why it is expected to generate only satisfactory solutions *in addition* to empirical data".

MIRI tends to believe that large chunks of AI theory are missing to design reliable AI algorithms, and those tools are what their research program aims to develop.

-> The missing AI theory chunks will fill the gap of understanding. 


2. 

*"AI that is build to reliably affect things in the world needs to have **world models that are amenable to inspection**"* 
 -> We do not know how to build "inspectable" world models. Such model should be multi-level. We do not have algorithm to do such thing for now.
  
 
 3. 

To solve in practice you need to approximate a brute force solution. If you can't you are probably missing some important conceptual tools.

-> Find a brute-force solution to any RL problem (Hutter & Legg) 
-> making it mature enough to work on practically (DeepMind) 

The point of MIRI is to develop the formal understanding of the pb in order to create the basic concepts and methods that are usefull for solving the problem (even though such methods will not be directly applied (e.g. full tree search vs heuristics in chess AI))
-> The introductory question shows the holes in the conceptual understanding. Solving such pb in theory (MIRI) will help them be solved practically later.


4. 
Rephrasing of the q: *"can we reduce the pb of building a beneficial AI to some other simpler pb?"*
E.g: *"can reduce the diamond maximization problem to known reasoning and planning procedures"*



