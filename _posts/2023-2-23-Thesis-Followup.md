## Thesis Topic Questions 2.0

From the last set of ramblings about my thesis options it is clear that I need to edit the list and again list the questions I have.

### Questions

#### Factual Errors 

- How are factual errors detected in text? 

- When local coherence is eroded and factual errors are made, is the mistake attributable to the attention?

- Does increased output or prompt length affect MIPS? Are errors more detectable in short text? If so, is this because the query vector is diluted?



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






