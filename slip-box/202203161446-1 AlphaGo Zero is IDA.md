Previous: [[202203161446 - IDA for game AI]]
Source: [[]]
Consider: [[]]
Tags: #game_ai #ida 
______________

The best move prediction is done recursively using a MTCS. Once the game done, the predictor is retrained over its games. Therefore we are in typical situation of iterated amplification (MTCS) and distillation (retraining).

![[Screenshot from 2022-03-23 07-12-46.png]]