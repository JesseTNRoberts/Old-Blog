## Reading about MusicLM, considering writing a survey on ICL, and how can we generate long sequences?

I started by reading the paper regarding audioLM. This paper preceeds the MusicLM paper. The method used in audioLM is a hierarchical sequence to sequence model. It is called hierarchical because audio clips are discretized to create a vocabulary. Then, a w2vec-Bert model is trained to do a MLM task. So, this model learns to "understand" audio sequences. They report that the audio recreations made directly by this model are somewhat coarse (?) but it does learn important long term and short term dependencies. So, the recourse was to layer on an additional model which would use the coarse generation as a seed that would then be used to fill in the coarse missing audio. These audio tokens are then used to build the finer audio output. In this manner, the model is a pipeline of 3 distinct models, the first of which is a language model that speaks discretized music.

AudioLM: a Language Modeling Approach to Audio Generation

