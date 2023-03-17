## Combining Encoder only and Deconder only architectures: Theoretically cooking with gas

A transformer architecture which is composed of an appropriately trained pair of encoder-only and decoder-only modules such that the decoder is turing complete and the encoder is coopetively trained to compress the output will be more computationally powerful than the sum of the encoder and decoder parameters suggests. That is, the number of parameters needed to reach a certain functionality will be less for the theorized system, than the number of parameters needed in a decoder-only model. 

The reasoning here is that, while non-erasing Turing machines are universal, they tend to consume significantly more tape (unproven) than an erasing Turing machine. Wang 1957 says that it is an open question whether a non-erasing Turing machine could use no additional space and only use four basic tape operations and remain computationally universal. It seems reasonable (unproven) that as the number of operations goes up, the number of additional spaces which must be consumed is reduced. A reasonable conclusion from this is to achieve desired functionality without operational artifacts (auxillary computation squares on the tape) the number of required operations is a function of the complexity of the task. 

This is actually a reality for transformer systems like chatGPT. A common method for achieving more favorable results in the face of complex reasoning is to required the model to produce operational artifacts. While these models are very powerful, they simply have not inferred sufficiently specialized operations to accomplish these more complex tasks. That does not imply that they cannot be solved by the model at all, but that the network must use auxillary computation squares to compute the results of subtasks. Then the task can be solved by performing simpler operations across the subtasks.  

So, if a system was desired which minimized auxillary computation squares, theoretically, a model which was formed using the a decoder only and ecoder only transformer architecture could do so without inflating the set of required (and largely idiosyncratic) operations. Essentially, this would permit compression and deletion which (unproven) functionally decouple the number of number of operations from the length of tape consumed. 


Theory: For a non-erasing Turing Machine to consume no auxillary computation squares, it must possess a number of instructions which tends to infinity. 

Approach to proof: for any task which requires no auxillary computation squares given a set of operations that does not include erasing or overwriting, there exists t' which requires at least one auxillary computation square. Further, for t' there exists a set of operations (not including erase or overwrite) which, if added, make t' computable without auxillary computation squares.

### The importance of the delete function

So, for a machine with restricted output form such that auxillary computation squares are not an option, the machine must possess a sufficient set of operations to perform the task. The sufficiency of the set is dependent upon the task. Therefore, for a non-erasing machine with any predefined set of operations to simulate a Turing machine, it must have unfettered access to auxilliary computation squares. Wang inversely states the same thing:

> The generalization consists in the waiving of the restriction that the initial input and final output tape contents must be of certain preassigned forms which are taken according to an ad hoc convention...

Therefore, a proof of Turing completeness which assumes an unrestricted output form where in practice the output is restricted without the presence of a delete or overwrite operation is insufficient to establish computational expressiveness. 

This shows explicitly the importance of the ability to delete when the format of the output is restricted.

### Neural Networks are non-algorithmic

Neural networks are given both a computational problem and the form of the complete output. Thus, the algorithm does not infer how to use a predetermined set of operations and scratch space to achieve functionality as is the case when designing a program for a Turing machine. Rather, the neural network must learn a set of operations which is capable of generating the output without any auxillary computation squares. Typically, this is done by scaling up the dimensionality of the input into a latent space that permits direct computation. However, scaling up into higher dimensions is simply a way of saying, a domain specific set of operations is learned which is capable of computing the output without auxillary computation squares. 

So, neural networks are precisely non-erasing Turing machines with restricted output format. It follows that neural networks may be computationally universal under assumptions which expect unrestricted output format and length. However, when restrictions are applied, an increasing set of operations are needed to perform an increasingly complex set of operations to actually perform compuational tasks. The result is a need for ever deeper neural networks which are capable of more and more operations. 






