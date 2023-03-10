Me: 
I think it brings new elements in favor of "search can be very messy" because it proposes some definitions of optimization where it is not possible to make a clear distinction between the optimizer and the "optimizand".

I have the intuition (need to think more about it) that pure heuristics are linked to this idea of an optimizing system where the optimizer cannot be clearly defined as a specific subcomponent

(but I really need to think more about this because I still use the old search concept to refer to optimization here)

I am currently wondering if the term "mesa optimizer" should be avoided and replaced with "implicit search"

Marius Hobbhahn  [8:35 AM](https://serialignment-qo78019.slack.com/archives/D04MT54S93K/p1678433711630709)  
I think mesa optimization is a super category of implicit search and thus they are not replaceable

Pierre Peigné  [9:08 AM](https://serialignment-qo78019.slack.com/archives/D04MT54S93K/p1678435696262109)  

You are right. But I think that using "search" as the definition of optimization is bad.  
I'll send you my thoughts on why think so in the evening. I'm currently writing things down about this.

The idea is that what we care about is more the configuration target of the optimizing system than how it reach it.  
If the system is performing search or not does not change the fact that it can be inner misaligned.

I do agree that it exists very important differences between searchy and non searchy optimizing systems (edited) 

But at the end of the day, what we want to know is whether we can understand the "decision process" of the optimizing system (if there is such a thing) and thus we would like to find a search/planning engine

Marius Hobbhahn  [9:14 AM](https://serialignment-qo78019.slack.com/archives/D04MT54S93K/p1678436061700429)  

right but planning isn’t the same as search, is it? Also, what if my network does other forms of optimization? I think they might be relevant as well. So I’d not support narrowing it down to search

but feel free to send me your thoughts. I’m busy over the weekend, so I might not read it for a while

Pierre Peigné  [9:14 AM](https://serialignment-qo78019.slack.com/archives/D04MT54S93K/p1678436097925559)  

I think that planning is a subset of search

(I can be wrong about this)

Marius Hobbhahn  [9:15 AM](https://serialignment-qo78019.slack.com/archives/D04MT54S93K/p1678436131855059)  

yeah not sure

doesn’t seem obvious to me but haven’t thought about it in detail

Pierre Peigné  [9:16 AM](https://serialignment-qo78019.slack.com/archives/D04MT54S93K/p1678436183295509)  

may be "run time optimization" is closest to what I want to pinpoint

Last thing I wanted to say is that you are totally right about the fact that limiting to search is bad because it does not take into account other forms of optimization. However, the canonical definition of mesa optimization is exactly based on search!

(so in some sense when we use this concept, we are narrowing down in a way we probably do not want to)

Marius Hobbhahn  [9:19 AM](https://serialignment-qo78019.slack.com/archives/D04MT54S93K/p1678436379376209)  

where in the post do they say that? I think they just use search as an example, not as a narrower subset

Pierre
We will say that a system is an optimizer if it is internally searching through a search space (consisting of possible outputs, policies, plans, strategies, or similar) looking for those elements that score high according to some objective function that is explicitly represented within the system.
Intro to "Risk from learned optimization"

(and I think that this is also from this that definition that I derive my understanding of planning being a subset of search)

Marius Hobbhahn  [9:22 AM](https://serialignment-qo78019.slack.com/archives/D04MT54S93K/p1678436577598739)  

fair enough

maybe all the “non-search” examples of optimization I have in mind are kind of searchy in nature

Pierre Peigné  [9:24 AM](https://serialignment-qo78019.slack.com/archives/D04MT54S93K/p1678436663041059)  

I think the gist is in "looking for those elements that score high according to **some objective function that is explicitly represented within the system**."

And given that part of the definition, probably most of the "non-search" examples (like heuristics) does not rely on an internal evaluation using some explicit objective function

This is precisely why heuristic are useful: because they are shortcuts

They approximate the "best" outcomes given a specific objective function but in a distilled way which suppress the need for evaluating them at run time

Marius Hobbhahn  [9:29 AM](https://serialignment-qo78019.slack.com/archives/D04MT54S93K/p1678436945229069)  

I think you’re on to something. Feel free to write down this argument in more detail. I think I could be convinced ![:slightly_smiling_face:](https://a.slack-edge.com/production-standard-emoji-assets/14.0/google-medium/1f642.png)