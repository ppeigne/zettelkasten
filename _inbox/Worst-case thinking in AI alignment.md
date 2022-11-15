Source: https://www.lesswrong.com/posts/yTvBSFrXhZfL8vr5a/worst-case-thinking-in-ai-alignment
Consider: [[]]
Tags: #worst_case #adversarial_optimization #abundant_bad_things #generalization_via_pessimistic_assumption #biggest_marginal_impact_strategy #murphyjitsu
______________

# Claim
It is important to make a distinction in the argument implying worst-case scenario.

# Key takeaways
- Adversarial optimization means being optimized against. If bad outcomes exists (even if extremely rare) they will have a high probability to be selected by the adversarial optimization process.
- Abundance of bad things means that the optimization process is not adversarial but the bad outcomes are sufficiently abundant to make a serious threat of being selected by the selection process.
- Pessimistic assumption concerns the fact that pessimistic strategies generalize better. Not relying on things working well makes the results more robusts.
- Biggest marginal impact strategy means that if your model of P(doom) is lower than 50% it is still good to work on 50% failure scenarios because this is where the marginal impact is the biggest (derivative of the logistic curve is maximized at 50%). Conversely people with P(doom) > 50% should focus on more optimistic scenarios. 
- Murphujitsu is concerns the heuristic of imagining counterfactual where everything got wrong to get a sense of what could go wrong.