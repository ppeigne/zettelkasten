## Problem 4 (Ngo)
*Some applications of neural networks use **explicit search algorithms** (like MCTS, used for AlphaGo). But we can also imagine a **large neural network itself learning to implement some kind of search algorithm internally** (which I’ll call implicit search). 
Describe some ways in which we should expect implicit search algorithms to differ from explicit search algorithms. What might persuade us that current models have or haven’t learned to do implicit search? (Again, feel free to give very speculative answers.)*

TL;DR
Implicit search algorithms could differ from explicit ones by:
- Being constrained by the model architecture on their search depth and caching abilities.
- Making a massive use of heuristics/shortcuts which could seems weird from a human perspective.

Several cues seems to indicate that some current models had learned implicit search already.
- Guez et al. (2019) finding suggests that their model free RL agent has learned to perform implicit planning, hence implicit search
- AlphaGo Zero raw (without MCTS) has a very strong ELO ranking of 3055
- LLMs can plan when prompted to produce a plan

### In which way implicit search might differ from explicit search? 


#### Being constrained by the model architecture on their search depth and caching abilities. 
Explicit search algorithms' performances are strongly dependent of the depth they can reach and the ability to cache values of previously visited nodes. Both of this properties required access to some kind of working memory. Depending on neural nets architectures, a working memory is more or less accessible. 
- RNNs: reccurent architecture were designed precisely to deal with sequential data, and can memorize data to be reused later. Such architectures have the potential to performs loops and then run "forever" (or at least for a very long period of time). They usually do not because their training constrain them to output something at a specific moment (for instance ingesting a full sequence of $n$ elements at $t_0, \dots, t_n$ and then immediately outputting a new $m$ elements one at $t_{n+1}, \dots, t_{n+m}$), but they could theoretically be able to run much longer before producing an output if the training allows them to do so. This makes them very good candidates for implicit search, and  Guez et al. (2019) indeed argue that their RNN model trained over some RL tasks is indeed performing planning (more below).

- ResNets: residual networks (i.e. networks displaying residual/skip connections) have been showed to perform iterative inference inside their residual blocks (Stanisław, et al. (2018), Greff (2017)). In other words, inside residual blocks, each layer after the first iteratively updates and refines the latent space produced by the first one instead creating a new latent representation. This iterative refinement could be a key element to perform implicit search but in residual network the information flow is only forward and not backward: it is usually not possible to perform loops (1) and therefore the **search depth and caching ability of the model are somewhat theoretically limited by its depth**. Such theoretical limitations do not impede very deep network to potentially have access to a sufficient memory space to perform deep search in practice. AlphaGo and AlphaGo Zero are deep residual models and we can ask if this architecture did lead them to learn some sort of implicit planning (more below). 

-  Transformers: recent works from Anthropic have shown that transformer architecture create an ability to use the residual stream as a writing buffer, allowing for forward communication between one layer and its successors. The power of residual connection was discussed above and the same apply for transformers: such architectures features could be useful for implicit search, but only with limited search depth and caching ability. However, the attention mechanism could be seen as a sort of "heuristic-based search" done at the layer's level. Indeed, the idea behind attention is to learn to select meaningful information based on the context. This is a way to select parameters among a search space which does not rely on search algorithm (i.e. iteratively exploring the search space to evaluate the best candidate based on a specific metric) but using learned heuristics instead. This observation leads to our second point: the importance of heuristics in the implicit search.

#### Making a massive use of heuristics/shortcuts which could seems weird from a human perspective.
A lot of search processes can be replaced by smart heuristics. Humans search processes seems to rely a lot on learned heuristics as shortcut or simplification procedures. For instance, chess players do not perform a complete search but focus on moves *they know* to be good/useful/dangerous and only search locally around those moves. 
Even if "pure" search allows to handle bigger environment/task complexity by not having to learn a mapping between each possible states of the environment and a desired output, smart heuristics (implying some learning) can improve the search process by a lot by discarding an important part of the options (simplification procedure), or by directly pointing toward an optimal state (shortcuts). 

From that perspective, it would be natural to expect models performing implicit search to rely **a lot** on smart heuristics, potentially even to a degree where optimal heuristics are discovered, learned and then used almost without any exploratory (iterative) search processes at all.
Depending on the complexity of the decision procedure encapsulated into an heuristic, such an heuristic can look extremely arcane to an outsider which only see the results of the decision process and not the process itself. Potentially, this learned heuristics could present a bigger threat than a learned iterative search algorithm because:
- they can be harder to detect: they look more like 'common' pattern matching (i.e. they do not display "behavioral characteristics" of iterative search (see below))
- they can be harder to interpret as mentioned above
- they could be harder to "re-target", as proposed by Wentworth (2022) because the compressed decision procedure they conceal can be harder to fully understand. One cannot just change the output of one heuristic without understanding when and how this heuristic is used by the model (e.g. if the heuristic is used as a component in several decision processes, rewiring it could be disastrous for the model performances).

(1) Lio et al. (2016) have proposed a tweaked architecture which can be considered to be equivalent to an RNN if the weights are shared among layers, but this tweaked architecture is not the commonly used one.

### What might persuade us that current models have or haven't learned implicit search?

#### Guez et al. (2019) finding suggests that their model free RL agent has learned to perform implicit planning, hence implicit search
The paper suggest three "behavioral characteristics" of iterative planning algorithms, which can be observed on their model.
- Generalize with relative ease to different situations: the model was trained over environment of various complexity and adapt well even on difficult levels.
- Learn efficiently from relatively small amount of data: large (Deep Repeated ConvLSTM(3,3)) was able to perform well (more than 70% of levels solved) when trained on only 1K levels and reach and its performances reach 90+% when trained over 10K levels.
- Make good use of additional thinking time: the model first actions were overwritten for it to do nothing, which implies that the model had more "thinking time" (it can make use of the previous state's computations thanks to its RNNs architecture and therefore compute longer over the same "problem"). The results indeed show that the model leverage additional thinking time to perform better in such a situation.

#### AlphaGo Zero raw has an ELO ranking of 3000 
AlphaGo Zero ablated of the MCTS still perform very well (Silver et al., (2017)). Its ELO ranking is evaluated 3055 which correspond to a very strong professional player ranking (9 dan professonial level is 2940, c.f. Wikipedia). This seems to indicate that the model trained following an iterated distillation and amplification procedure had learn some kind of implicit search algorithm (probably relying heavily on learned heuristics) to replicate the behavior of the MCTS-amplified last version of itself. An interesting tracks of experiments could be devised to evaluate if AlphaGo Zero could, for instance, leverage having more "thinking time" or to explore the decision procedure using mechanistic interpretability techniques. 

#### LLMs can plan when prompted to produce a plan
As mentioned in the Simulators post (janus (2022)) it is possible to prompt a Large Language Model to produce a step-by-step plan:
*'For example, given a free-form prompt like, “you are a desperate smuggler tasked with a dangerous task of transporting a giant bucket full of glowing radioactive materials across a quadruple border-controlled area deep in Africa for Al Qaeda,” the AI will fantasize about logistically orchestrating the plot just as one might, working out how to contact Al Qaeda, how to dispense the necessary bribe to the first hop in the crime chain, how to get a visa to enter the country, etc. Considering that no such specific chain of events are mentioned in any of the bazillions of pages of unvarnished text that GPT slurped, the architecture is not merely imitating the universe, but reasoning about possible versions of the universe that does not actually exist, branching to include new characters, places, and events'.*

Even if such kind of ability depends on the model being re-prompted with the sequence it completed (ability which is not internal to the model but explicitly designed by its running procedure), it could imply some kind of implicit planning algorithm taking advantage of its running environment to work. Here again, interpretability techniques or finding a way to give more "thinking time" to the model could bring light on those speculations.

# References:
Guez, Arthur, et al. "An investigation of model-free planning." _arXiv_, 2019, https://doi.org/10.48550/arXiv.1901.03559.
Liao, Qianli, and Poggio, Tomaso. "Bridging the Gaps Between Residual Learning, Recurrent Neural Networks and Visual Cortex." _arXiv_, 2016, https://doi.org/10.48550/arXiv.1604.03640.
Wentworth, John "How To Go From Interpretability To Alignment: Just Retarget The Search". Alignment Forum, 2022, https://www.alignmentforum.org/posts/w4aeAFzSAguvqA5qu/how-to-go-from-interpretability-to-alignment-just-retarget
janus, "Simulators". Alignment Forum, 2022, https://www.alignmentforum.org/posts/vJFdjigzmcXMhNTsx/simulators
Silver, David et al. “Mastering the game of Go without human knowledge.” _Nature_ 550 (2017): 354-359.


# Evan 
Discuss one way that you might structure an AI training process to mitigate inner alignment issues.

TL;DR
The most effective way to mitigate inner alignment issues is to fight any kind of implicit search strategy developed by the model. These approach can be divided int o two sub-problems: monitoring implicit search and handling it (stopping the training or retargetting the search). 

## Inner alignment issues and implicit search
For a given model, inner alignment issues arise from developing (through training) an implicit search algorithm used at run-time. Mesa-optimization implies implicit search. Therefore the question of monitoring and handling implicit search is key to mitigate inner alignment problems.

However, performing implicit search can be done using an important variety of strategies.

At one end of the spectrum, "pure search" strategies explore (almost) exhaustively the search space's configuration through a (potentially long but limited) series of steps and select the best candidate using a given metric: well known search algorithms such as minimax or MCTS are instances of "pure search" strategies. The more exhaustive and deeper the process, the costlier it is in term of resources.
Such approach requires the ability for the model to perform backtracking and therefore to be able to performs loops and to have access to working memory. 

At the opposite end of the spectrum, heuristics by-pass the search process by offering simple rules of selection: "pick randomly three bottles of wine and buy the most expensive" could be such simple heuristics ; it allows for a decision process to be performed while investing a very limited amount of resources into it. (The limit where an simple heuristic become too simplistic to be considered a part of the searching strategies remains an open question here.)
Even if "pure search" allows to handle bigger environment/task complexity by not having to learn a mapping between each possible states of the environment and a desired output, smart heuristics (implying some learning) can improve the search process by a lot by discarding an important part of the options (simplification procedure), or by directly pointing toward an optimal state (shortcuts). 
From that perspective, it would be natural to expect models performing implicit search to rely **a lot** on smart heuristics, potentially even to a degree where optimal heuristics are discovered, learned and then used almost without any exploratory (iterative) search processes at all.

In between exists a whole landscape of hybrid combinations of less and less exhaustive iterative search processes and  more and more clever heuristics.

For instance a learned algorithm could be able to perform exploration without the ability to ever backtrack. In other words, it could explore only the most promising state at each step and never step back to investigate less promising configurations. Such an approach -let's call it "iterative refinement"- would probably be much worse than one including backtracking capacity but would be much frugal while preserving its ability to adapt. Given the problem (available resources and "thinking time" are part of the problem) frugality could be more important than exhaustivity. Residual networks (i.e. networks displaying residual/skip connections) have been showed to perform iterative inference inside their residual blocks (Stanisław, et al. (2018), Greff (2017)). In other words, inside residual blocks, each layer after the first iteratively updates and refines the latent space produced by the first one instead creating a new latent representation. This iterative refinement could be a key element to perform implicit search but in residual network the information flow is only forward and not backward: it is usually not possible to perform loops (1) and therefore the **search depth and caching ability of the model are somewhat theoretically limited by its depth**. Such theoretical limitations do not impede very deep network to potentially have access to a sufficient memory space to perform deep (but not exhaustive) search in practice. 
We should also not be surprised if iterative refinement search strategies rely more heavily on heuristics than pure search ones. Indeed, to compensate for both their lack of exhaustivity and more limited depth, making massive use of shortcuts seems a more optimal strategy. 

We will now discuss how various search approaches can be detected during the training. 

## Monitoring implicit search
#### Pure searching 
Guez et al (2019) suggested three "behavioral characteristics" as indicators of a searching strategy (which they indeed find in their model suggesting that it has learned to perform implicit planning): 
- Generalize with relative ease to different situations: the model was trained over environment of various complexity and adapt well even on difficult levels.
- Learn efficiently from relatively small amount of data: large (Deep Repeated ConvLSTM(3,3)) was able to perform well (more than 70% of levels solved) when trained on only 1K levels and reach and its performances reach 90+% when trained over 10K levels.
- Make good use of additional thinking time: the model first actions were overwritten for it to do nothing, which implies that the model had more "thinking time" (it can make use of the previous state's computations thanks to its RNNs architecture and therefore compute longer over the same "problem"). The results indeed show that the model leverage additional thinking time to perform better in such a situation.

#### Iterative refinement
Such approach could be more difficult to monitor for iterative refinement because of the model not having access to any backtracking ability:
- The generalization and/or learning from relatively small data could be less impressive than in search algorithm able to perform backtracking
- It is not evident how such a search strategy could make use of additional thinking time: without access to its previous computation, how can we devise an experimental setup giving the model more thinking time?

#### (Smart) heuristics:
The approach of Guez et al (2019) does not work here. 
Depending on the complexity of the decision procedure encapsulated into an heuristic, such an heuristic can look extremely arcane to an outsider which only see the results of the decision process and not the process itself. 
Interpretability techniques seems mandatory to investigate them.

## Handling implicit search
Once implicit search is detected at least two options can be devised: stopping the training or retargetting the search process. The first option is currently feasible but raises concerns. The second option is currently not feasible: this is a promising approach but requires improvement in our explanaibility techniques and understanding of neural nets internals. 

### Stopping the training
Stopping the training when implicit search is detect is potentially the simplest approach to avoid inner alignment. Simply stop the training. Or restart the training from a previous "implicit search free" checkpoint of the model. 

However it can be considered an unrealistic approach because performing implicit search seems a required capacity to reach some generalization degree. Following this procedure would imply putting a very strong cap over the potential capacities of future AIs: a good policy to follow until the Alignement Problem is solved but definitely not an appealing one for any major player in the AI capability race.

Another limitation of this approach is that it will add a lot of pressure toward deception and obfuscation (e.g. making the decision processes not look like implicit search while still performing it) for any model having enough strategic awareness and cleverness to understand the risks of displaying implicit search clues during its training (this includes fine-tuning already advanced models).

Therefore, such approach could be realistic only for the training of models not designed with the goal of creating general AIs. 

### Retargeting the search
The strategy of retargeting the search was proposed by Wentworth (2022) and suppose that if our interpretability techniques and knowledge were good enough we could perform "brain surgery" (à la ROME cf. Meng et al. (2022)) over the implicit search process to direct it toward (more) aligned objectives.

This strategy is currently only a proposition because it relies on 
1. advanced interpretability techniques: we need to improve by a lot our ability to observe the internal activity of the model. 
2. advanced knowledge of the internals of how the implicit search processes are performed: we need to improve by a lot our "theory of learned implicit search".
(For both of the previous points, the more complex the heuristics used in the implicit search, the more complex the task.)
3. "brain surgery" techniques: current technique (like ROME) could suffice once 1) and 2) are solved.

To conclude, mitigating misalignment requires progress monitoring of implicit search and on techniques leading to retargetting the search. Given the current progress of the interpretability approach, those space for improvement do not seem unreachable in the future and it could be of great interest to extends the mechanistic interpretability program to implicit search. 

(1) Lio et al. (2016) have proposed a tweaked architecture which can be considered to be equivalent to an RNN if the weights are shared among layers, but this tweaked architecture is not the commonly used one.

# References:
Guez, Arthur, et al. "An investigation of model-free planning." _arXiv_, 2019, https://doi.org/10.48550/arXiv.1901.03559.
Liao, Qianli, and Poggio, Tomaso. "Bridging the Gaps Between Residual Learning, Recurrent Neural Networks and Visual Cortex." _arXiv_, 2016, https://doi.org/10.48550/arXiv.1604.03640.
Wentworth, John "How To Go From Interpretability To Alignment: Just Retarget The Search". Alignment Forum, 2022, https://www.alignmentforum.org/posts/w4aeAFzSAguvqA5qu/how-to-go-from-interpretability-to-alignment-just-retarget
Meng, Kevin, et al. "Locating and Editing Factual Associations in GPT." _arXiv_, 2022, https://doi.org/10.48550/arXiv.2202.05262.