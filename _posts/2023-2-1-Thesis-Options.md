## Language Models, rhetoric, narrative, and self talk

The following are the general ideas/topics I have come up with
- Inclusion and exclusion of information via executive function
- Long range dependencies and coherence via abstractions and low frequency information
- Using abstractions to manage attention (to facilitate external control via symbolic AI)
- Using the prompt (or output or output as prompt) as working memory

Idea from Dr. Fisher:

- Using an algorithm to do prompt engineering for experience management ala *Interactive Narrative:
An Intelligent Systems Approach*

This can be seen as a specific type of executive function in which the objective is more abstract and dynamic.


## Developing My Thesis Topic: Executive function, abstractions, and working memory in language models

Consider this as a nugget: the need for language model control systems


### ICL Prompts and output as working memory

One of the questions around large language models is whether they can learn to include and exclude things with executive oversight based on an objective. 

The most prevalent mechanism for interacting with a language model is prompting. In this way, the prompt acts as a working memory for the objective. Then the output from the model can also be considered working memory for verbal decomposition and reasoning. This is a very interesting perspective on working memory as it is reminiscent of Turing's early memory implementations which were simply resonant tubes which would "remember" the pressure wave, from one end of the tube to the other. Thereby, effectively implementing a delay. 

This comparison may be telling. In the case of the Turing machine, the machine is able to read cells in the tape, write cells, and edit cells. Language models are currently only able to write and read cells. So, given an objective in working memory and some output from the language model, there is no ability to amend the working memory correct deviations away from the objective.

A model that may be able to do this is described below which uses the strengths of CLM and MLM to achieve this. <ins> A way of systematically testing this would be to perturb the output of the model and evaluate subsequent decisions to either edit and correct the deviation or to continue generation.</ins>

The introduction of abstractions is important to applying transformers to other more abstracted tasks (like narrative generation). Without the ability to manipulate abstracted narrative and expositional tokens, building a narrative will be too computationally expensive. Specifically, the rate of growth of parameters as compared to the input size is quadratic. Current technology would likely require more than a google $10 \cdot 10^{100}$ of parameters to attend to the number of necessary tokens. So, if each atom in the universe were a parameter, there still wouldn't be enough to write *The Picture of Dorian Gray*.



- What do we know about ICL and how it works?


- What are the requirements for the pretraining task? the representation? 


- How does term frequency in the pretraining, term frequency in demonstration labels, and task to label distribution disjunction affect ICL?


- Can ICL be used to for NLU beyond semantic structure? Can it be used for things which specifically depend on semantic structure? Can it be used for things which specifically depend on syntactic structure?


- Can ICL infer and apply strict rules?


- What is the status of ICL visualization and prompt based explanation?


It seems that a finetuned model for classification should be more closely attending to the prompt than a model which is simply generating new text. The reasoning is that a generative model is focused on attending to the new text to create local coherence. This is not the case with a finetuned model. However, it is possible that in reality the pretrained model has just as much attention on the prompt until multiple tokens have been generated. 

Perhaps this is the reason that MLM are better at NLU. They learn to attend very closely to the prompt with little self-attention. 

- <ins>When local coherence is eroded and factual errors are made, is the mistake attributable to the attention? </ins>

If a language model attends to the prompt it may make errors regarding local coherence. Is it typical that local factual errors and local coherence errosion coincide with attention primarily on the prompt?

#### Paper: Are Sixteen Heads Really Better than One?

One of the results from this paper is that most attention heads in the multiheaded attention system are not necessary. Through ablation, the authors show that most heads can be removed without statistically significant effects on model fitness. 

An interesting and notable exception to this is the cross attention layer between encoder and decoder. These attention heads have more dramatic and rapid effects on model fitness when ablated. This is somewhat predictable as attention heads here manage attending to generated text versus attending to the prompt. 


#### Prompts across models

- Are prompt/label pairs which are more successful on one model or class of models successful on other models and classes? (Does good on GPT-2 imply good on GPT-3? Does good on GPT-2 imply good on BERT?)



#### Hierarchical Structure in Text 


##### Long sequences 

Transformers work based on attention to prompt and the output from the decoder. 

- (Answered) ~~So, given attention can only be placed on the input and output of certain length, how can transformers generate long text and attend to the entirety?~~

The answer is simple. Currently, they can't. The max input and output length of GPT-3 is 2049 tokens (or about 1500 words). Many important texts are far longer than this. So, the limitation is fairly major. If we had powerful language models that were only built to generate short lengths of text, could these models be smaller and formed hierarchically to account for longer generation (ie generate an outline, then generate the text for each piece of the outline)? Another way of saying this is, could language models be trained to attend to information that changes at different rates (author changes more slowly, than topic, which changes more slowly than sentence meaning, which changes more slowly than the actual words).

- (Answered) What is the relationship between input and output length, model fitness, and number of parameters? (if the model's power is primarily in the number of pararmeters without considering the size of the input and output, then decreased input and output is not useful)

Current technology has a quadratic growth in number of parameters (as well as space and time complexity) with respect to the size of input. On the other hand, there is no theoretical relation between model size and perplexity. The intuitive hypothesis is that language models which accept longer inputs are able to better consider the context and predict words in light of this context. This is only a hypothesis. But it does seem to be readily testable. 

The question here is, do language models with more parameters have lower perplexity because they are better able to consider the context? The null hypothesis is that language models with many parameters achieve lower perplexity because they have learned something which the smaller model has not. There must be some plateau beyond which no further improvement can be gained by model size. 

This is persuasive to some degree as chatting is a specifically low context situation and it is what openAI seems to think is the best applicaion of GPT-3.


- What resolutions of time varying information are captured by language models? (author, topic, rhetorical structure and intent, sentence meaning, words)

One way that this could be assertained would be through second hand learning (something I just made up). The idea is that language models learn so much that it may be possible to train a second model from the language model. By considering the last 7 words to be "working memory" and the tokens attended to  beyond this and their positions to be representative of the topic, a dataset of word to generate based on working memory and topic could be constructed! Also, we can infer the topic for the current token based on the long range dependency (maybe?). Then, a model could be trained that would accept a prompt, a topic or sequence of topics, and working memory to generate the next token.

- Another way of asking the question immediately above is what frequency information is learned by transformed architectures?

Consider that the author or topic is a value which changes slowly relative to words in the sequence. Another way to say this is the probability distribution over the values in the time varying sequence is dependent on the low frequency amplitude values. So, if one were to take the fourier tranform of the sequence, they would find that the low frequency amplitudes were correlated with certain time series values. 

It is now obvious that transformers learn significant content about the time series and are very good at predicting next values. The question is, do they latently learn frequency transforms to make use of this slower changing bias?

The problem is, I'm asking a question about the latent representational content. The only way I can see to actually address this would be to evaluate the latent space and look for patterns which seem to correlate with the desired signal. One way is to consider the current output word in a CLM to be the signal, and then look at the latent space for patterns. Post-hoc analysis of the generated text should yield topical information which could be used to look for signals in the latent representation that capture topic. Then as a follow-up, we could artificially adjust the latent representation to have activation more similar to the topics which have been identified to evaluate if this changes the likelihood of certain words. 


- Can these more slowly changing abstractions be used to achieve long term coherence in large texts?

The answer here is that rhetorical writing and narrative writing definitely would benefit from this. In these the only important information is the rhetorical or narrative effect of surrounding sections and the intended rhetorical or narrative effect of the current section. 

- Is there a means of measuring macro-coherence as well as micro-coherence? 

Language models may trade prompt attention (attending to the objective) for attending to the micro-coherence of the generated response. As the response length grows, it may be harder to attend to both effectively (hence incorrect responses to the prompt in favor of semantic similarity based responses and errors in details in generated text). 

Perhaps both could be attended to through abstractions.


### What work has been done on long document NLU and NLP?

- How can experiments regarding potential models be conducted? 

At scale train and test of a new transformer model can cost 10's of thousands of dollars. With that being the case, is there a reasonable method for creating and evaluating new models in a limited fashion? 

#### Paper: Do Long-Range Language Models Actually Use Long-Range Context?

In this paper the authors explore the information actually accessed and used in two types of long range attention models (local transformers and routing transformers). The benefit reported is somewhat predictable. Local transformers don't actually have long receptive fields, rather they are simply localized. Routing transformers cluster over things to which need to be attended. 

The results show that perplexity is reduced only on tokens that are relatively infrequent. This should have been anticipated as tokens with higher frequencies will appear in shorter receptive fields.

The idea here can be inherited from signal processing. The minimum sampling rate for a signal is twice the max frequency. A token that occurs with frequency k with k = 1/(mean tokens between samples) will only be guaranteed to be in the receptive field if the receptive field is at least 2/k tokens in size.

So, unchanged perplexity on more frequent tokens should have been obvious. 


#### Paper: Efficient Content-Based Sparse Attention with Routing Transformers

It is important to note that this work is only applicable to CLM.

Looking into the paper referenced in the previous paper, it seems that routing transformers have been proposed by google. The underlying idea is content driven (context dependent) sparse attention. 

From analysis contributed by other papers, it is clear that the benefit to perplexity is specific to those tokens which occur at lower frequencies. It begs the question, could attention heads be encouraged to attend to tokens that occur at different frequencies?

The authors make the point that:

> local attention sparsity variants are effective in practice since correlation between observations naturally decrease with time for many problems

While this is the case, it is not generally true. Specifically, in narrative and rhetoric. Further, while it may be true that correlation dimenishes with temporal distance between tokens, it is not true that the correlation between lower frequency concepts like topic experience reduction. 

Further, it seems appropriate to evaluate models along a measure that may be refered to as topical perplexity. This seems related to the task given to BERT where it was asked to declare whether a sentence was a successor or not. That is a very good idea. Hierarchically defined perplexity (or perplexity at varying time scales as opposed to only token - high frequency - level perplexity). 





#### Attention is all you need... for open loop language generation (No Executive Control)

Attention provides a mechanism for direct forward generation of text (causal LM) and for forward inference in NLU (MLM). However, it does not provide a mechanism for evaluation of the generated text in light of the objective and revision. This would constitute a type of closed loop control. 

##### <ins>Idea: Using an MLM to act as the feedback loop for a CLM in text generation in response to a prompt</ins>

MLMs are shown to be more well suited for NLU while CLMs tend to be more well suited for text generation. The idea then is simple, use a CLM for generation and after each generated token blank a number of previous tokens and ask the MLM to fill in the blanks based on the prompt and the generated text so far. Each of the actions (edit and concatentate) could be considered in series (with the MLM sometimes opting to change nothing) or both actions could be considered simultaneously with the chosen action being sampled from the overall logits.   


## Narrative to Narrative

With the introduction of systems that are manipulating tokens in a hierarchical fashion while making use of transformers (AudioLM) it seems more an more possible to directly generate narrative tokens, followed by exposition tokens, and then finally textual tokens. 

This is directly supported by the lines of research above which look to understand the inherent representation of abstracted information (topics, et al) and the effort to add executive function in the form of planning to language models. 


## How human are Language models?

It seems that humans have things in common with both LMs and RNNs. Humans don't have the ability to hold 2049 tokens in their working memory. However, it is not the case that they only intake a single token without working memory. 

### Do they think like us?

### Do they make mistakes like us?

ADD 


