## Thesis Topic Questions 2.0

From the last set of ramblings about my thesis options it is clear that I need to edit the list and again list the questions I have.

### Questions



#### Architectural Details and Attention

- (Answered) What is the effect of the residual connection in cross attention coming from the decoder?

It forces the residual bias signal to have the statistics of the decoder rather than the encoder (which actually wouldn't change as the encoder input is typically fixed). So, as the generation progresses, the autoregressive decoder has shifting residual bias rather than a static bias from the encoder. 

This is also the mechanism used for attentional blending (or whatever you call the summation and normalization of decoder self attention and cross-prompt attention). 
  
- (Answered) What is the effect of the key and value vectors coming from the encoder?

Key and query vectors are identical in treatment. So, it would be no different to have the query vector come from the encoder. The keys and queries are used to select values (somewhat obvious). So, having either keys or queries come from the encoder allows the encoder to help guide selection. On the other hand, values coming from the encoder means that the encoder output is what is being attended to in cross attention. So, the architectural construction of the cross attention implies the question: 

given the output, how should the prompt be attended to? 

So, cross attention in the traditional encoder architecture should be more correctly referred to as cross-prompt attention. 

Then the residual connection acts as a blending of attention on the prompt and generated output to achieve the next output. 

This begs a subsequent question, why not also allow the question "given the prompt, how should we attend to the generated text?" To do this, another parallel cross attention layer would be needed in which the values come from the decoder. The residual connection would still come from the decoder because the effect is attention blending. 



- (Answered) In encoder only models, I assume cross attention is eliminated as it is in decoder only models. However, this raises the question, is there actually a difference in encoder only/decoder only or is the deciding factor causal access to tokens? 

This point is actually important because otherwise, the origin of keys, values, and queries in the decoder is left ambiguous.

The answer is yes, decoder only/encoder only models differ on their masking primarily. There's a good discussion on this in *Exploring the Limits of Transfer Learning with a Unified Text-to-Text Transformer*. One of the things that is also apparent in their discussion is the limited meaning of language model. They consider language model to refer specifically to single stack transformers (regardless of encoder or decoder only, which is to say regardless of masking). In fact they go so far as to say that language models are limited to next token/word prediction models. ie. causality is incumbant upon language models. 

Within this taxonomy, BERT is not a language model. 


- Are decoder only models capable of being Turing Complete?

##### On the Computational Power of Transformers and its Implications in Sequence Modeling

The authors of the above paper, show that transformers are Turing complete. And they show that the residual connection from the decoder around the cross attention layer is necessary. Without the cross attention residual connection the transformer is not capable of being Turing complete. 

##### Overcoming a Theoretical Limitation of Self-Attention

In this paper the authors show that transformers are incapable of learning to recognize a parity language. The reason is because as the input string length grows large the cross entropy grows toward 1 such that classifying boolean strings as parity odd or even tends toward a random guess. 

I believe the same thing occurs when transformers make factual errors. The cross entropy grows large and it becomes difficult to separate factual n-grams from incorrect n-grams. 


- How can transformer architectures be tested in a computationally tractable scenario such that success in the tractable implies the level of success at scale?

Can transformer architectures be studied without spending hundreds of thousands of dollars to implement them at scale?

Obviously, for a test to be meaningful to large scale language application, the smaller testing language must have similar statistical structure to the target language. So, generic sequential data wouldn't prove generalizability. 




- Is residual connection an effective means of attention blending? 

Less work has been done using the full transformer architecture. More has been done using encoder or decoder only systems. Attention summation forces equal weight on both cross-prompt attention and decoder self-attention. So, in training, errors are not contextualized to be blaimed on the probable attentional origin. They are blaimed on both attention sources. I'm not sure if this is good, bad, or neither.


#### Questions about the literature


- Is there a good taxonomy and survey of NLP NLU transformer architectures? 

This should not consider the obvious (parameters, layers, attention heads), instead it should consider the details of each model (residual connections, normalization, dimensionality of query vectors, attention sparsity). It should consider task suitability of the architecture (language modeling, denoising, summarization, generation, etc). Further, it should consider pre-training signals and tasks as well as the masking. 



- Is there a good review of the current state of large ablation studies for replicability? 

Bertology has become common to an extent. However, the systematic study of transformer architectures does not seem to have an appropriate review available. 


- Has there been a study of relative scaled-down transformer models? 




#### Factual Errors 

- From a MIPS perspective, what is a factual error?

Factual correctness may require different attention than a conversational system. 

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

Type of closed loop control (a piece of executive function).
Also, a type of computational critic.


  - Use a combination of MLM contextual divergence and CLM perplexity to evaluate textual interestingness 


- Measure MLM understanding of a word in context via context relevant information attributable to the word (via KL divergence)

Called contextual divergence


- Generate and identify rhetorical structures (including chiasmi) via transformer model

computational rhetorical criticism


- Long narrative generation with experience control

  - The encoder of the generic architecture could be replaced with an algorithm used to adjust the topic of generation enforced upon the decoder. (potential control system connection point)

  - Use decoder only model and output buffer management (like asymptotically increasing entropy) to generate stories 


- Implement cross-generative attention (described above)

- Attention Dilution may account for errors and topic loss

- Add information to transformers by adding a database that is accessible via MIPs to augment and facilitate domain specific knowledge 

- Successive Addition of Attention heads 


#### Papers

- ICLR paper on the Turing Completeness of Decoder only Transformer models 

Working on this this morning. I have convinced myself that it is reasonable to demonstrate. The demonstration is straightforward from previous work. Esstentially, the full transformer was shown to be Turing complete by showing that the transformer could simulate an RNN. However, the question of whether this would apply to a model like chatGPT was open until now. The reason is because language models use only the decoder portion of the model. 

To show the decoder portion alone is Turing Complete, one only needs to show that the decoder only portion of the model can simulate the full transformer architecture, which has been shown to be capable of simulating an RNN, which is known to be capable of simulating any Turing Machine a la siegelmann and sonheim.

The proof is made possible by multiheaded attention and learned sparsity/universal approximation in the feedforward network. 

- Survey on transformers 

  - Need to find an angle

    - Narrative Generation
    - Theoretic Understanding
    - Scientific Understanding

- AI Magazine article: OpenAI isn't solving the alignment problem. They are applying an idiosyncratic censor.

This will eventually lead to problems. People trusting the system will be beguiled into a false sense of security. 

- Attention Dilution in transformers as a method to explore the effect of varying attention on preference relations 

- upsampling representation of individuals in a population for fair selection (stylometric generation and computational social choice)

For any selection algorithm with any bias and any definition of fairness, there exists a semantically equivalent, fair transformation of the input data such that the end to end selection (with the transformation and selection algorithm) is fair. 

