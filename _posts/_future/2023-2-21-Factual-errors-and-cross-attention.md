## Understanding factual errors in language models with respect to attention


The hypothesis is that factual errors are correlated with attention. Specifically, it may be that factual errors occur when attention is not on the prompt. 

I now think that this may not be the case. 

First, a language model's attention is a type of maximum inner product search. The cross attention blends the attention on the prompt and the output. The result is a set of vectors that map into a hyperspace. In the resulting space that is returned by the blended MIPS, factually correct statements are not far apart. So, more domain specific knowledge may be helpful but it may be also that the vector space is simply not sparse enough to maintain factual correctness and general conversence. 






