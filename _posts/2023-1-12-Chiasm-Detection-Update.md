## Chiasm detection update

I have completed the first experiment regarding identifying chiasma via GPT-3. The experiment is a zero shot learning experiment using no fine tuning and instead using patterned prompts. The results are not specifically compared to the existing body of work yet. However, they look promising.

A few thoughts:
- This is the lowest power version of applying large language models to this question. 
- The labels used to identify chiasma were chiasm and not chiasm. 

Using labels in this way triggers my memory regarding the use of unsupervised learning as a pretraining for a supervised task. The data must have distribution appropriate to the supervised labels. Otherwise, the learned model won't be well suited to subsequent supervised training. 

In this case the language model is attending to the pattern in the prompt rather than being trained. The prompt has a pattern of labels applied to clauses. It seems possible that the label used and the concept which is to be labeled could be mismatched in a potentially destructive way (similar to the unsupervised pretraining problem). This raises the question, for language models, does the label used in a zero shot learning scenario affect the results of the model? Or, to put it elegantly, does a rose by any other name smell as sweet?

Questions to evaluate:
- How did the language model compare to the existing literature? New state of the art?
- Does the language model seem to consider the intent of the author or merely the collocation of tokens?





