## Thesis Topic Questions 2.0

From the last set of ramblings about my thesis options it is clear that I need to edit the list and again list the questions I have.

### Questions



#### Architectural Details

- What is the effect of the residual connection in cross attention coming from the decoder?

In some architectures, the residual connection comes before layer normalization. 


- In encoder only models, I assume cross attention is eliminated as it is in decoder only models. However, this raises the question, is there actually a difference in encoder only/decoder only or is the deciding factor causal access to tokens? 

This point is actually important because otherwise, the origin of keys, values, and queries in the decoder is left ambiguous.

The answer is yes, decoder only/encoder only models differ on their masking primarily. There's a good discussion on this in *Exploring the Limits of Transfer Learning with a Unified Text-to-Text Transformer*. One of the things that is also apparent in their discussion is the limited meaning of language model. They consider language model to refer specifically to single stack transformers (regardless of encoder or decoder only, which is to say regardless of masking). In fact they go so far as to say that language models are limited to next token/word prediction models. ie. causality is incumbant upon language models. 

Within this taxonomy, BERT is not a language model. 

- Is there a good taxonomy and survey of NLP NLU transformer architectures? 

This should not consider the obvious (parameters, layers, attention heads), instead it should consider the details of each model (residual connections, normalization, dimensionality of query vectors, attention sparsity). It should consider task suitability of the architecture (language modeling, denoising, summarization, generation, etc). Further, it should consider pre-training signals and tasks as well as the masking. 





#### Factual Errors 

- How are factual errors detected in text? 

- When factual errors are made, is the mistake attributable to the attention?

I think that this may be the case in CLMs. It could be the case that as text grows long, it dilutes the query vector.

  - If so, are errors more detectable in short text? 



#### Language Model Planning and Control

- What would be needed for a language model control system (executive function) for various objectives?

- It may be that controlling language models for various purposes (narrative experience vs content exclusion vs factual correctness) is non-monolithic. However, it is probable that they share similar needs. 


- How can information be excluded or included?

- What would be needed to manage a narrative experience?



#### Turing Completeness and Working Memory

- What would be needed for language models to be Turing complete (memory?)?


- Does the length of output in ICL and topical drift affect the model? If so, is the output well suited to be working memory? When should the prompt be revised for continued reasoning?



#### Few shot learning

- How does term frequency in the pretraining, term frequency in demonstration labels, and task to label distribution disjunction affect ICL?

- Are prompt/label pairs which are more successful on one model or class of models successful on other models and classes? (Does good on GPT-2 imply good on GPT-3? Does good on GPT-2 imply good on BERT?)



#### Low frequency informational content

- What resolutions of time varying information are captured by language models? (author, topic, rhetorical structure and intent, sentence meaning, tokens)

- Can slower changing signals in the text be used to achieve long range coherence in narrative and rhetoric?


#### Sparse attnetion, long range connections, and low frequency terms

- Are the results from bertology (Are sixteen heads really better than one?) consistent routing transformers?



___
### Ideas

- MLM evaluation and revision of CLM generation

- Measure MLM understanding of a word in context via context relevant information attributable to the word (via KL divergence)

Called contextual divergence

- Use a combination of MLM contextual divergence and CLM perplexity to evaluate textual interestingness 

- Correlation of errors with length of output, cross attention, and query dilution

- Generate and identify rhetorical structures (including chiasmi) via language model

- The encoder of the generic architecture could be replaced with an algorith used to adjust the topic of generation enforced upon the encoder. (potential control system introduction)




