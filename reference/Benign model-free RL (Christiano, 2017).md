Source: https://www.alignmentforum.org/s/EmDuGeRw749sD3GKd/p/PRaxzmDJdvie46ahL
Consider: [[]]
Tags: #reinforcement_learning #benign #model-free #ida #robustness
______________

Training end-to-end benign model-free agent (or subsystem) using IDA needs: 
- a benign expert $H$
- an efficient reward learning procedure + a training procedure preserving robustness
- a working solution to capability amplification

It is important to be able to detect if the agent is just benign with high probability or truly (boolean = 1) benign.