# Setup experimental  
Introduire tous les personnages qui vont jouer dans la piece de theatre. Leur donner des noms et les contextualiser brievement.

### Context general - zoom I  
*Défini dans la decription initiale du projet, rarement mis a jour en cours de projet*  
Quelle partie du monde tu observes?  
#interp Quel modele tu etudies? Quelle est son architecture? Sa training procedure?Potentiellemnt pointeur possible si deja decrit auparavent

#### Model
- 2 layers attention-only transformer
```
'd_head': 64,
'd_mlp': 128,
'd_model': 128,
'd_vocab': 128,
'd_vocab_out': 2,
'n_heads': 2,
'n_layers': 2,
'positional_embedding_type': 'standard'
```

#### Training procedure
##### Dataset
Sample pattern: 
`V1;V2;V3-#IDX:V4-V1;V2;V4"` (example where IDX correspond to pos 3 in the list)

- Generate 2048 samples per batch.
	- 1/3 good samples
	- 1/3 samples with a wrong value: the updated element in the list is not equal to `V4` but to another value `V5`. 
	- 1/3 samples with a wrong idx: the position of the updated element in the list does not match the position indicated by `#IDX`

*The wrong samples are created by changing either the idx or the value of one of the good samples. In other words for each good samples, two additional wrong samples are provided.*

##### Training
- Loss: binary cross entropy
The model is trained for up to 10_000 epochs but stop if it got an accuracy of 1 during 50 consecutive epochs.


### Zone de focus - zoom II  
*Vaguement défini au debut, mis a jour 2-3 fois au cours du projet*
De ce gros systeme, sur quoi tu te concentres? Introduit la terminologie des objets que tu va reutiliser lors de l'analyse. Potentiellement donne des sources d'ou tu tires de la terminologie qui n'est pas clair lorsque le projet a commencé. Cela contenir des découvertes des jours precedent sur lesquelles tu creuses pendant plusieurs jours.

Attente: un glossaire, des schema avec des noms (e.g. le nom de position particuliere dans une sequence.)
#interp C'est l'endroit ou tu decrit la sous-distribution que tu etudie / le phenomene.

###### Studied phenomenon
The circuit developped by the model to solve this task. 
It implies 

###### Glossary
### Zone d'etude courante - zoom III  
*Zone d'etude qui change presque tous les jours. ~ 5-15 min.*  
Aujourd'hui qu'est ce que tu as etudié. Sur quel sujet d'etude se concentre les experiences decrite ci dessous?

## Methode experimentale
### Comment tu modifies le monde?  
*beaucoup de techniques sont redondantes, ne change pas tres souvent.*  
De quelle maniere tu interagit avec la partie du monde étudiée? Quelles inteventions? Potentiellement vacante si pas de modification du sujet d'etude mais uniquement de l'observation.(Pas description precise d'experience)*Structure attendue: une bullet point de techniques et leur definition si necessaire (e.g.un schema d'intervention)*

### Qu'est ce que tu measure?  
Quels sont tes yeux? Observes tu des images, des nombres (en quelle unitées?) Quelles mode d'observation? Quelle metrics, quelles measures?Be clear about what metric you're using, and give extreme examples (what is 0% what is 100%) to explain what is measured and what it’s not.
Quelle sont les valeurs de baseline de ces mesure? Quels ordre de grandeur a s'attendre?
*Structure attendue: une bullet point de methodes et leur definition si necessaire (e.g. une formule )*

# Best guess d'une histoire  
Potentiellement vacante (~ si >3 jours en interp, une histoire -- même simple -- doit exister).  

Quelle est l'histoire de comment les personnages interagissent pour le moment? (incorpore les resultats de la capsule, I WANT TO BE SPOILED.) L'histoire peut contenir des partie comme "et là, je sais pas, je suis confu." 
Il est tout a fait possible d'avoir plusieurs histoire independantes aussi.

*Structure attendue: un schema / courte description de comment les personnages intergagissent entre eux. L'effort a deployer peut être grand, mais le but est que cela force a aggreger les differentes observation en un tout coherent. ~ 30-60 min. Il est cependant probable que ce travail ait été deja fait dans le passé mais pour cette section les pointeur ne sont pas authorisés. Tu **dois** repasser le temps a examiner les parties de l'histoire que tu tiens pour acquis, même celles dont tu ne penses pas concernées par les experiences de la capsule a priori.*

# Observations
Structure attendue: alterner entre  
* Description detaillée de l'experience  
* Utiliser les pointeurs vers les definition ci dessus.  
* Resultats  
* A cote de chaque resultats faire une prediciton sur la proba que ce resultats vienne d'un bug ou d'un artefact quelconque qui n'est pas du tout ce que tu imaginais (i.e. you were not measuring what you thought you were). Pour des raison d'accountability / d'estimation de la fiabilité des resultats. Cela peut simplement être un gut feeling de "ces resultats sont vraiment trop bizarre, c'est probable qu'il y ait un bug."  
* courte interpretation  
* Quelles partie de l'histoire ces resultats update / confirme ?  
* Est ce que c'etait un resultats attendu? Ou un resultats suprenant par rapport a ce que tu t'attendais? (mettre les predictions passées si les experiences faisaient partie de "next steps" de capsules passées.)  
* * **En gras, mettre les resultats suprenants.**# Next steps##### Planned next steps  
*Question that should be answered. Before clear your cache and answer it. C'est crucial que les next steps sont en effet les plus pertinents.*Quelles sont les questions les plus importantes a repondre?  
Quelles experiences peuvent repondre a ces questions?  
Qu'est ce que tu t'attends a apprendre de ces experiences?  
A quoi ca ressemble si ces experiences ne fonctionnent pas et te donne presque aucun bit d'information? A quel point est ce que c'est probable?  
Quels sont les axes sur lesquels tu compte pousser? (e.g. plus de modele differents, tester si les resultats generalise a d'autre distribution, garder le meme objet d'etude mais changer les methodes, aller en profondeur dans l'analyse actuelle sans changer le setup experimental etc.) Noter cela principalement lorsque l'axe sur lequel tu pousses change par rapport au jours precedents.Faire des predictions. Prendre un sous ensemble d'experiences que tu comptes realiser, concretiser leur definition et faire une prediction sur leur resultats.  
* e.g. proba de resultats X de l'experience E est 50%.Quels est la durée de realisation des experiences? Y a t il un moyen d'avoir des données similaire (peut être marginalement de moindre qualité) plus rapidement? i.e. quelle vitesse tu peut toucher la realité?