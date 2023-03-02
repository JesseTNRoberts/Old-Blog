## Potential Collaborations Discussion

From the meeting a few interesting things did result. 

1. First, for new language models to be built at scale, it will likely require a level of evidence that is similar to what is necessary for clinical trials. However, the markers which suggest success at mass scale are not clearly understood. Less so, the markers that suggest new and interesting behavior. 

New architectures can inherit confidence from existing transformer models like chatgpt. However, the question is will a language model that is encoder only or encoder/decoder only do something that is interestingly different from chatgpt?

2. Can a sufficiently trained decoder only transformer model be prompted sufficiently to generate text representative of any genre?

3. Can a decoder only transformer model be passed a prompt sufficiently to implement long term memory?

One way that this could be done would be to keep the global prompt and an ongoing summary of the generated text at the top of the buffer, but the rest of the buffer act as a FIFO. In this way, the model would continuously attend to the newest information while having abstracted representations of older generated text. It could even be that abstraction happens continuously. So, being further from the generated token means higher and higher entropy. In this way, all information stays in working memory. Though, very old things may have significantly unrecoverable information due to the level of compression. 


## Thoughts on The Alignment Problem

If Brian Christian is correct in his assessment that humans will never be able to hide unwanted information from an AI, that the AI will always "hear the shoes on the floorboards", then the answer seems simple. Pit Holmes against Holmes. For an individual with k protected classes, use adversarial learning to generate k versions of an individual such that 
