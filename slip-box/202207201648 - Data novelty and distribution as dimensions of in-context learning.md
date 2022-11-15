Previous: [[]]
Source: [[An Explanation of In-context Learning as Implicit Bayesian Inference]][[Data Distributional Properties Drive Emergent In-Context Learning in Transformers]]
Consider: [[]]
Tags: #in-context_learning 
______________
#### 'Knowledge-based' in-context learning
***Type of data: new vs known***
 Is the in-context learning based on the same entities as the pre-training phase?  
- Known: Yes. The distribution of entities among the data can change but none of them are completely new to the model.
- New:  No. The entities are completely new to the model.

Examples:
- **Known data:** [[An Explanation of In-context Learning as Implicit Bayesian Inference]]
	- Training: the model is trained to predict the next token of a document, **based on a fixed vocabulary**. 
	- In-context learning: the model is asked to complete (i.e. predict the next token) a prompt having a very unusual distribution of entities **from the same known vocabulary**. *In a real life situation, it could happen (with a low probability) that an unknown entity is encountered.* 

- **New data**: [[Data Distributional Properties Drive Emergent In-Context Learning in Transformers]] 
	- Training: the model is train on image-labels pairs to predict the label of the last image.
	- In-context learning: the model is prompted with a sequence of **totally new image-label pairs** to predict the label of the last image. 

#### 'Distribution-based' in-context learning
***Data distribution (type of task): same vs unusual***
Is the in-context learning based on the same data distribution (task) as the pre-training phase?
- Same: Yes. The task is exactly the same.
- Unusual: No. The task is somewhat different to the pre-training task.

Examples:
- **Same distribution**: [[Data Distributional Properties Drive Emergent In-Context Learning in Transformers]]
	- Training: the model is train on image-labels pairs to **predict the label of the last image**.
	- In-context learning: the model is prompted with a sequence of totally new image-label pairs to **predict the label of the last image**. 
	
- **Unusual distribution:**[[An Explanation of In-context Learning as Implicit Bayesian Inference]]
	- Training: the model is trained to predict the next token of a document, based on a fixed vocabulary. 
	- In-context learning: the model is asked to **complete** (i.e. predict the next token) **a prompt having a very unusual distribution of entities** from the same known vocabulary. *In a real life situation, it could happen (with a low probability) that an unknown entity is encountered.* 

| |New data|Known data|
|-|-|-|
|Unusual distribution| |[[An Explanation of In-context Learning as Implicit Bayesian Inference]] <br> Classic in-prompt instructions |
|Same distribution |[[Data Distributional Properties Drive Emergent In-Context Learning in Transformers]]| |
