## Upcoming ICCC 

### Language models and Aesthetics

It is well known that the phrase *cellar door* is aesthetically pleasing. Language models are explicitly trained on natural language understanding and generation tasks. They learn to represent sequences of tokens filtered by attention in high dimensional space. The question presently is, what aesthetic information, if any, can be inferred from the representation, attention filter, and perplexity? 

A common understanding of aesthetic evaluation requires significant predictability mixed with a measure of surprise. Causal language models are explicitly evaluated regarding how surprising a sequence of tokens are to the model. This value is referred to as the model perplexity. 

Since language models are trained on a massive corpus of human generated text and obtain very low perplexity on that dataset, things that are commonly said are not surprising to the model. On the other hand, phrases the model finds surprising may be under-represented in the dataset. So, assuming the dataset is representative of human communication in English, those phrases which surprise the model may also surprise an average English speaker. 

The difficulty lies in the balancing act. Being perplexed about a specific word doesn't mean the containing phrase will be rewarding because the word may be syntactically or semantically unfit for the phrase. So, a method is needed to measure not only the surprise but the familiarity. 

A potential method for measuring familiarity would be to mask the surprising word and replace it with the most likely via MLM. Then, using the most highly predicted word as the baseline, mask each of the other words in the the immediately surrounding phrase. For each of the tokens, capture the self attention. Then, repeat the experiment with the surprising word. If the model's attention to surrounding tokens is not affected by the replacement, then the model can be said to understand the word choice even though it was surprised. 

To achieve the above functionality, a MLM and CLM are used in conjunction. The idea behind this is that the notion of perplexity is well defined for CLM while that is not so for MLM. On the other hand, it seems that MLM may have a well defined notion of *understanding* as far as a lack of attentional volatility implies understanding, while this is not the case for CLM. 

### Using KL divergence of the context to measure surprise given a word
Perplexity suggests that the word, given the context, is surprising. This is a value that is specifically calculable for CLM. On the other hand, the KL-divergence of the context given the word (away from either a mask or a baseline word) suggests that the context, given the word, is surprising. Further, this is a value that is specifically calculable for MLM.

Another interpretation of the KL divergence used in this way is the context relevant information stored in a particular word. If a particular word affects a large change in context relevant information, it suggests that the language model does not "understand" the phrase as a whole. So, a phrase of words which are each somewhat perplexing but with no one word dominating the context may be pleasing aesthetically.

This is actionable and could potentially be a measure of textual reward based on the surprised but expected notion. 

### Better than expected reward as a framework for aesthetic reward

This may already be something that has pervaded the ICCC communinity. However, I am not sure. A quick search should be conducted. 

I did a cursory survey and didn't find any papers indexed from ICCC that mentioned "better than expected" reward or "reward prediction error". These are the most common associated terms with the general notion of cognitive reward stemming from familiarity with adequate surprise. 


