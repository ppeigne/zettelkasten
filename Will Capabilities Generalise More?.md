Source: https://www.lesswrong.com/posts/cq5x4XDnLcBrYbb66/will-capabilities-generalise-more
Consider: [[]]
Tags: #advanced_capabilities #intelligence_explosion 
______________

# Key takeaways
Question the argument for wether capabilities generalize further alignment once capabilities start to generalize far at all.

For:
1. Capabilities have much shorter description length than alignment
   The simplicity prior leads to encountering good approximation of general intelligence before good approxiations of alignment.
   
2. Feedback on capabilities is more consistent and reliable than on alignment
   The consistency of the feedback for capabilities will produce a bigger pressure toward being competent than toward being aligned.

3. There's essentially only one way to get general capabilities and it has a free parameter for the optimization target
   What the capabilities are directed over is path- and prior-dependent in a way which is currently not understood. We do not know how to design the path and prior such that the goal is reached robustly.

4. Corrigibility is conceptually in tension with capabilities, so corrigibility will fail to generalise when capacity generalize well
   Corrigibility creates obstacles in the algorithm plans. Get around with obstacle is what we expect a competent general AI to do. Therefore, our model will have incentives to find breaches than to generalize well over such obstacles. 
    
5. Empirical evidence: human intelligence generalized far without staying aligned with its optimization target
   
6. Empirical evidence: goal misgeneralization happens
   
7. The world is simple whereas the target is not
   The world is structured by simple laws. On the other hand human values are very complex. A good model of the world will therefore priviledge simplicity of its world model and not learn values.
   
8. Much more effort will be poured into capabilities (and d(progress)/d(effort) for alignement is not so much higher than for capabilities to counteract this)
   
9. Alignment techniques will be shallow and won't withstand the transition to strong capabilities
   a) we do not understand well what alignment means in strong capabilities regimes, b) we do not have the ability to refine our techniques by iterations once in the stronc capabilities regime

Against:
1. Optimal capabilities are computationally intractable; tractable  capabilities are more alignable.
   If optimal capabilities are not reachable. Tractable capabilities could be easier to aligned because they could not rely on optimal planning.
   
2. Reality hits back on the models we train via loss function based on reality-generated data. But alignement also hit back on models we train, because we also use loss functions (based on preference data). These seem to be symmetrically powerful forces.
   Working on non-harful and non-deceptive AIs is done even without thinking about x-risks. Therefore, it exists a strong pressure toward being aligned.
   
3. Alignment only requires building a pointer whereas capability requires lots of knowledge. Thus the overhead of alignment is small, and can ride increasing capabilities.
   Training is more costly than finetuning (if you consider that finetuning is alignment...)
   
4. We may have schemes for directing capabilities at the problem of oversight, thus piggy-backing on capability generalisation
   Overseer are asymmetrically advantadged. 
   
5. Empirical evidence: some capabilities improvements have included corresponding improvements in alignment.
   Finetuning (if you consider it to be alignment...) is make possible by increase in capabilities.
   
6. Capabilities might be possible without goal-directedness
   You can use tool AIs. (But will we?)
   
7. You don't actually get sharp capability jumps in relevant domains
   Optimization on economically relevant domains will reduce the overhang by a lot and therefore smooth the curve of capabilities. Therefore the alignment schemes will be applied only to slightly better AIs.