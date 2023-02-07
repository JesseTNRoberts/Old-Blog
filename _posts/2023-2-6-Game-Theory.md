## Connecting Game Theory Work to LLM

- Does the text generated from language models exhibit symptoms of ADD? Could this related to the attention on the prompt and working memory?

I think that it should. The reason is because LMs don't have the ability to abstract and symbolically manipulate topics to create macro-coherence. So, limited memory forces partial attention. When the parial attention is not on the prompt, the model is likely to generate text that begins to diverge from it. 

The example I encountered regarding the prisoner's dilemma is telling. The prompt did not represent a prisoner's dilemma. However, the semantic structure of the prompt resembled the formulation of a PD. So, the model generated the words prisoner's dilemma which were then attended to more highly than the actual prompt (as the strategy recommended was based on text regarding a PD). Essentially, generated coherence was considered more important to attend to than correctly addressing the prompt. 

I wonder if finetuning a language model changes the attention tendencies? It seems like it should. The reason being, if a model is finetuned to classify sentiment, it begins to know that the length of output sequence will be short and it should more heavily attend to the prompt instead of shifting attention to the generated text for the purpose of coherence.  

From the above, perhaps the right way to make the connection is in the opposite direction. Perhaps language models and how they work actually help explain the rationale in the TD. Attention starts on the prompt (the global context of possible strategies) then attention shifts to local reasoning given the prompt. The first step of generation selects an area of the strategic space and then forward reasoning is conducted with coherence considered more important than optimization. Then, the agent attends to the local and fails to simultaneously attend to the global context which induces uncertainty. This uncertainty causes weak domination to collapse into FWD at a local level. 


## Finishing my work on the traveler's dilemma

- In what contexts is iterative reasoning more evolutionarily stable than wholistic reasoning?
- Show that iterative reasoning in non-deterministic computational time and space results in uncertainty regarding the weak domination of strategies
- Uncertainty in weakly dominated strategies makes the use of FWD reasonable

## Connections: To clinical diagnosis

There are interesting connections that can be drawn regarding theory of mind from the above. If an agent attempts to make sense of the actions of another agent while assuming that the other agent has unrestricted computational space and time, the agent will likely impute incorrect reasoning. As an example, in the case of the traveler's dilemma, choosing 100 can be seen as a risky decision while choosing 2 can be seen as a risk averse decision. However, the resulting choices can be shown to arise from the same preference relation which is insensitive to risk. Rather, the two strategies are chosen based on the agent's access to computational time and space. 

More about this is written in other places. 




