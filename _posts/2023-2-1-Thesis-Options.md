## Developing My Thesis Topic: Executive function, abstractions, and working memory in language models


### ICL Prompts as working memory

One of the questions around large language models is whether they can learn to include and exclude things with executive oversight based on an objective. The most prevalent mechanism for interacting with a language model is prompting. In this way, the prompt acts as a working memory for the objective. 

- What do we know about ICL and how it works?



- What are the requirements for the pretraining task? the representation? 


- How does term frequency in the pretraining, term frequency in demonstration labels, and task to label distribution disjunction affect ICL?


- Can ICL be used to for NLU beyond semantic structure? Can it be used for things which specifically depend on semantic structure? Can it be used for things which specifically depend on syntactic structure?


- Can ICL infer and apply strict rules?


- What is the status of ICL visualization and prompt based explanation?

- <ins>Evaluate the attention placed on the prompt both for pretrained and finetuned models</ins>

It seems that a finetuned model for classification should be more closely attending to the prompt than a model which is simply generating new text. The reasoning is that a generative model is focused on attending to the new text to create local coherence. This is not the case with a finetuned model. However, it is possible that in reality the pretrained model has just as much attention on the prompt until multiple tokens have been generated. 

Perhaps this is the reason that MLM are better at NLU. They learn to attend very closely to the prompt with little self-attention. 

#### Prompts across models

- Are prompt/label pairs which are more successful on one model or class of models successful on other models and classes? (Does good on GPT-2 imply good on GPT-3? Does good on GPT-2 imply good on BERT?)



#### Hierarchical Structure in Text 


##### Long sequences 

Transformers work based on attention to prompt and the output from the decoder. 

- (Answered) ~~So, given attention can only be placed on the input and output of certain length, how can transformers generate long text and attend to the entirety?~~

The answer is simple. Currently, they can't. The max input and output length of GPT-3 is 2049 tokens (or about 1500 words). Many important texts are far longer than this. So, the limitation is fairly major. If we had powerful language models that were only built to generate short lengths of text, could these models be smaller and formed hierarchically to account for longer generation (ie generate an outline, then generate the text for each piece of the outline)? Another way of saying this is, could language models be trained to attend to information that changes at different rates (author changes more slowly, than topic, which changes more slowly than sentence meaning, which changes more slowly than the actual words).

- What is the relationship between input and output length, model fitness, and number of parameters? (if the model's power is primarily in the number of pararmeters without considering the size of the input and output, then decreased input and output is not useful)


This question is really a piece of a greater question that is, can a language model with a smaller input/output field be used with abstractions over more slowly changing information (author, topic, etc) to achieve similar results and thereby reduce the cost associated with training?


- What resolutions of time varying information are captured by language models? (author, topic, rhetorical structure and intent, sentence meaning, words)

One way that this could be assertained would be through second hand learning (something I just made up). The idea is that language models learn so much that it may be possible to train a second model from the language model. By considering the last 7 words to be "working memory" and the tokens attended to  beyond this and their positions to be representative of the topic, a dataset of word to generate based on working memory and topic could be constructed! Also, we can infer the topic for the current token based on the long range dependency (maybe?). Then, a model could be trained that would accept a prompt, a topic or sequence of topics, and working memory to generate the next token.


- Can these more slowly changing abstractions be used to achieve long term coherence in large texts?


- Is there a means of measuring macro-coherence as well as micro-coherence? 

Language models may trade prompt attention (attending to the objective) for attending to the micro-coherence of the generated response. As the response length grows, it may be harder to attend to both effectively (hence incorrect responses to the prompt in favor of semantic similarity based responses and errors in details in generated text). 

Perhaps both could be attended to through abstractions.


#### Attention is all you need... for open loop language generation (No Executive Control)

Attention provides a mechanism for direct forward generation of text (causal LM) and for forward inference in NLU (MLM). However, it does not provide a mechanism for evaluation of the generated text in light of the objective and revision. This would constitute a type of closed loop control. 

##### <ins>Idea: Using an MLM to act as the feedback loop for a CLM in text generation in response to a prompt</ins>

MLMs are shown to be more well suited for NLU while CLMs tend to be more well suited for text generation. The idea then is simple, use a CLM for generation and after each generated token blank a number of previous tokens and ask the MLM to fill in the blanks based on the prompt and the generated text so far. Each of the actions (edit and concatentate) could be considered in series (with the MLM sometimes opting to change nothing) or both actions could be considered simultaneously with the chosen action being sampled from the overall logits.   




## What sort of RNN/LM combinations have been attempted?

It seems that humans have things in common with both LMs and RNNs. Humans don't have the ability to hold 2049 tokens in their working memory. However, it is not the case that they only intake a single token without working memory. 


