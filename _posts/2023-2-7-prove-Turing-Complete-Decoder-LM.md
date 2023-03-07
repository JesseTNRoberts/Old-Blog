## Turing completeness of transformer (decoder only) language models

Based on _On the Computational Power of Transformers and its Implications in Sequence Modeling_ and Siegell and Sonheim.

### Sketch of the proof

It has already been proven that RNNs are capable of simulating an arbitrary Turing Machine. Further, it has been shown that the vanilla transformer presented in Vaswani (with minor characteristic adjustments) is in turn capable of simulating an arbitrary RNN. Therefore, it is understood that the transformer architecture is Turing complete. The author's of previous work have discussed the implications of this. And it has been shown that there are hand built constructions of models capable of solving tasks that are difficult for transformers because they require fixation. 

The previous work does not necessarily apply to the decoder only language models as the architecture diverges from the vanilla transformer. The proof here is based on showing that it is possible for a decoder only language model to simulate an RNN. 

Consider a decoder only language model with two attention heads and a single layer. The input to the RNN is provided to the language model all at once (see previous paper). However, just as in the previous construction, a positional embedding is used to differentiate the timesteps. In the first decoder attention head, it learns to be time sensitive (previous paper) so that only the current time step input is passed along to the FFN at a given timestep. Further, the second attention head simply passes along the previous output (previous paper).  

The FFN is then tasked identically to the construction in the previous paper. Therefore, it is proved that decoder only language models are capable of simulating an RNN and are therefore Turing Complete.

This is an important result which furthers the theoretical understanding of powerful models on which chatGPT and other notable systems rests. 
