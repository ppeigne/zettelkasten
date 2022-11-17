---
cssclass: research-note
type: "webpage"
title: "Does SGD Produce Deceptive Alignment? - AI Alignment Forum"
citekey: DoesSGDProduce
---
“Does SGD Produce Deceptive Alignment? - AI Alignment Forum.” Accessed November 15, 2022. [https://www.alignmentforum.org/posts/ocWqg2Pf2br4jMmKA/does-sgd-produce-deceptive-alignment](https://www.alignmentforum.org/posts/ocWqg2Pf2br4jMmKA/does-sgd-produce-deceptive-alignment).
[online](http://zotero.org/users/10595302/items/9PQMKU8U) [local](zotero://select/library/items/9PQMKU8U) [pdf](file:///home/research/snap/zotero-snap/common/Zotero/storage/SMLZN3L8/Does%20SGD%20Produce%20Deceptive%20Alignment%20-%20AI%20Alignme.pdf)
 


# Key takeaways




### Index

start-date:: 
end-date::
page-no:: 1

### Connections

comment:: 

### Note
%% begin annotations %%
### Imported on 2022-11-16 2:05 pm
>[!quote|#5fb236] Reference
>
this episode of the AI Alignment Podcas [(p. 1)](zotero://open-pdf/library/items/SMLZN3L8?page=1&annotation=3JJPNCSW)
>[!quote|#ffd400] 
Claim
>
how likely deceptive models are to result from a particular training process [(p. 2)](zotero://open-pdf/library/items/SMLZN3L8?page=2&annotation=FY2UPJAH)
>[!quote|#a28ae5] Personal critic
>
Only a small number of objectives a model could have are equal to the base objective [(p. 3)](zotero://open-pdf/library/items/SMLZN3L8?page=3&annotation=HIUF9M78)
>[!quote|#ffd400] 
Claim
>
internally aligned models are highly improbable� [(p. 3)](zotero://open-pdf/library/items/SMLZN3L8?page=3&annotation=5IMI2PYV)
>[!quote|#a28ae5] Personal critic
>
Out of all possible pointers� there are only very few pointers that robustly point at a model of the base objective [(p. 3)](zotero://open-pdf/library/items/SMLZN3L8?page=3&annotation=YV9HVMKU)
>[!quote|#ffd400] 
Claim
>
corrigibly aligned models are also highly improbable [(p. 3)](zotero://open-pdf/library/items/SMLZN3L8?page=3&annotation=HK9X94UP)
>[!quote|#a28ae5] Personal critic
>
Because of instrumental convergence� there are many objectives that result in the model optimizing for the base objective� [(p. 3)](zotero://open-pdf/library/items/SMLZN3L8?page=3&annotation=U7NYLSIW)
>[!quote|#ffd400] 
Claim
>
deceptively aligned models are likely to be more numerous [(p. 3)](zotero://open-pdf/library/items/SMLZN3L8?page=3&annotation=EKR7IF6P)
>[!quote|#2ea8e5] Supporting evidence
>
As an analogy� we can consider the Christian God� who is trying to produce humans that are aligned with his values� One such person is Jesus� who has the same objective as God � he just fundamentally wants to do the same thing� Another such person is Martin Luther� who is aligned with God because he wants to study the Bible� �gure out what it says to do� then do that� Finally� we have Blaise Pascal� who is aligned with God because he thinks if he does what God wants he�ll go to heaven in the future� Correspondingly� there is only one Jesus because there is only one human objective that is exactly the same as what God wants� There might be a few Martin Luthers� but robustly pointing to the Bible is a di�cult task� so there are not going to be that many� However� anyone that believed what Blaise Pascal believed about God could become another Pascal� so there are many possible Pascal [(p. 3)](zotero://open-pdf/library/items/SMLZN3L8?page=3&annotation=MCH5XNI9)
>[!quote|#2ea8e5] Supporting evidence
>
To be explicitly� Jesus is internally aligned� Martin Luther is corrigibly aligned� and Blaise Pascal is deceptively aligned [(p. 3)](zotero://open-pdf/library/items/SMLZN3L8?page=3&annotation=T78FH5TV)
>[!quote|#ffd400] 
Claim
>
Given that a random model that optimizes for the base objective is likely to be deceptive� the default expectation is that the model that SGD converges to is deceptive� [(p. 4)](zotero://open-pdf/library/items/SMLZN3L8?page=4&annotation=XD36VV3P)
>[!quote|#ffd400] 
Claim
>
we argue that SGD systematically favors deceptive alignment� [(p. 4)](zotero://open-pdf/library/items/SMLZN3L8?page=4&annotation=M9MBT7CC)
>[!quote|#ffd400] 
Claim
>
SGD will take a large number of training steps to converge to an internally aligned model� [(p. 4)](zotero://open-pdf/library/items/SMLZN3L8?page=4&annotation=F6RLDXV7)
>[!quote|#ffd400] 
Claim
>
SGD will take a large number of steps to converge to a corrigible model� [(p. 5)](zotero://open-pdf/library/items/SMLZN3L8?page=5&annotation=2FFMLFB2)
>[!quote|#ffd400] 
Claim
>
A model becoming marginally more deceptive will marginally lower the training loss� A model that learns marginally more about the training process seems like it should get marginally more deceptive [(p. 5)](zotero://open-pdf/library/items/SMLZN3L8?page=5&annotation=HCJMVXEK)
>[!quote|#ff6666] Important
>
In general� �model the world better� is a very natural modi�cation for SGD to make to the model� In this sense� even if the marginal bene�t of modeling the training process better is unclear� it seems likely to happen incidentally as a result of natural model performance improvement� [(p. 6)](zotero://open-pdf/library/items/SMLZN3L8?page=6&annotation=8V5RGTPF)
>[!quote|#ff6666] Important
>
For example� if a model is being trained to predict text� some of the text it is going to predict is going to be about SGD� The model will have to understand how SGD works in order to predict that text properly� Thus� as a natural result of the training process� the model will learn to model the training process� potentially becoming deceptive� [(p. 6)](zotero://open-pdf/library/items/SMLZN3L8?page=6&annotation=6QHEIMBJ)
%%It seems that there is a missing step there.

1. Is understanding SGD really required to predict text about SGD properly?
2. Seems to be a gap between learning what SGD is and modeling the training process%%
>[!quote|#ff6666] Important
>
Since this pointer is built at runtime instead of by SGD� there might be more optimization power put into making this pointer robust [(p. 6)](zotero://open-pdf/library/items/SMLZN3L8?page=6&annotation=GZAWEYRI)
%%Do not understand the pointer at runtime%%
>[!quote|#ff6666] Important
>
Thus the marginal increase in deception might result in more optimization pressure being applied to building a robust pointer� causing SGD to favor deceptive alignment� [(p. 6)](zotero://open-pdf/library/items/SMLZN3L8?page=6&annotation=TE6L74IL)
>[!quote|#2ea8e5] Supporting evidence
>
In order for a model to be internally aligned� it must have a good model of the world� which is an approximately su�cient condition for deception� [(p. 7)](zotero://open-pdf/library/items/SMLZN3L8?page=7&annotation=5FDHZ6JU)
>[!quote|#2ea8e5] Supporting evidence
>
n order for a model to be corrigibly aligned� it must have a good model of the base objective� which is also an approximately su�cient condition for deception� [(p. 7)](zotero://open-pdf/library/items/SMLZN3L8?page=7&annotation=AUPRY56D)
>[!quote|#5fb236] Reference
>
Gradient hacking� is a strategy that a deceptively aligned model could use to preserve its current objective� [(p. 11)](zotero://open-pdf/library/items/SMLZN3L8?page=11&annotation=WPBP2NYQ) %% end annotations %%

%% Import Date: 2022-11-16T14:05:15.803+01:00 %%
