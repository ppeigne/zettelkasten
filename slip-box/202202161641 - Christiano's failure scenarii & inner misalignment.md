Previous: [[]]
Source: [[What failure looks like (Christiano, 2019)]]
Consider: [[]]
Tags: #inner_alignment #outer_alignment #failure #mesa-optimization #power-seeking 
______________

Are power-seeking agent the results of an inner or outer alignment problem ?

My first intuition was "inner alignment". It does not came from an analytical reasoning, more some kind of a "gut feeling".

After reasoning i was thinking more at an outer alignment problem: the problem come from an inability to design a proper goal for the AI. The objective function does not includes the "do-not-seek-influence" policy.

However Ngo present it as an inner alignment problem. Why ?
Does influence-seeking behavior arise from mesa-optimization only ?
In Christiano, the problem of mesa-optimization does not seems to be mentioned. 

The core description of the training is the following : 
*Modern ML instantiates _massive_ numbers of cognitive policies, and then further refines (and ultimately deploys) whatever policies perform well according to some training objective. If progress continues, eventually machine learning will probably produce systems that have a detailed understanding of the world, which are able to adapt their behavior in order to achieve specific goals.*

*Once we start searching over policies that understand the world well enough, we run into a problem: any influence-seeking policies we stumble across would also score well according to our training objective, because performing well on the training objective is a good strategy for obtaining influence.*

