## Experimental Questions

- Do transformer based PLMs possess representations which are sufficient for recognition of rhetorical structures?

- What is the optimal set of exemplars for few shot teaching for GPT-2 based system?
- What is the optimal set of exemplars for teaching BERT?
- Which of these perform best as exemplars for GPT-3 (assuming each set is unique). 

- Can language models expand expand the compact rhetorical meaning represented in structures like chiasma? (Good question but may be addressed in a follow up paper)

## Experimental Design

The easy experiment is to use exemplars for few shot teaching the language models. Then use the language model to classify the structures by presenting patterned cloze test questions to the model.

I am not yet certain how to identify the optimal, minimal exemplar subset beyond brute force. 

It is also not clear how one should ask a language model to expand the meaning of a rhetorical structure. This is a good idea. But I'm not sure that I want to address this in the first paper. 
