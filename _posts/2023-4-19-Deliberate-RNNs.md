## Deliberate RNNs

To restore the Turing completeness result for RNNs it is necessary to change the method by which they are applied as shown in previous work. A concrete method to restore this is described below. 

Using dropout we are able to get a measure of the certainty of a neural network. We may define an input to the network as the latch input. While this is high, the network should deliberate on the appropriate output. That is, the network should attempt to hold the output stable while the input is high. However, to do so, it will need to fight against the noise induced by randomized dropout. The output considered to be the final decision of the network is the output after a number $k$ of stable epochs during which the output changes by no more than $\epsilon$. 

In this manner the network will learn to use its last output to deliberate and come to a stable output. Stability is interpreted as certainty. By allowing deliberation to be unbounded in number of epochs, the network is capable of unbounded minimization. Therefore, the Turing completeness result is restored. 

An interesting question is, which is better, a predefined $k$ or a stochastic value of required stable epochs? 


### Training

It will be difficult to provide supervised training examples to such a network. Reinforcement learning may be preferred. 


### Being clear about the problem 

The problem being addressed is not that a trained network is not Turing complete. Rather, the problem is that an RNN in the manner typically used is not capable of learning partial recursive functions (or equivalently, general recursive functions). The reason is that RNNs can't learn unbounded minimization. Therefore, there are important classes of functions which are computable (in a Turing sense) but are not learnable.

To see this, consider a situation in which we want an RNN to learn a function that maps from input to output. However, the relationship involves unbounded minimization. We do not provide in process outputs and instead only provide the input and the final output. The input to the RNN may be a function and a value for which we are searching. We want the RNN to identify the input to the function which gives the target value or the closest value possible to the target. 

Further, we have a sequence of the inputs and want the RNN to learn the sequence of the outputs. 

The relationship is such that it is impossible for a network of defined size to learn the relationship without unbounded access to intermediate recursive calculations. This is a natural conclusion since the set of partial recursive functions are not primitive recursive. So, like the Ackerman function, they cannot be calculated using for loops of predefined size. Rather, they require unbounded loops (while loops).  

Assuming an algorithm exists which may inductively learn appropriate weights to encode an algorithm which will utilize the unbounded intermediate recursive calculations, we would prefer our network architecture be capable of implementing such an algorithm.  


### Is the problem in training? 

The problem is not in the training method. The problem is in the architecture. 

Assuming that a training method existed which could infer the algorithm needed for any problem and encode the algorithm in a set of inputs, interpreting the output of the network as the output of the algorithm or even as an element of the output sequence provided by the algorithm prevents the network architecture from being capable of implementing all computable algorithms. 

For the set of all computable algorithms to be implementable, an output is needed which is similar to the latent space of the network. That is, it is unconstrained by the user in terms of encoding and length. 

Past work in _Turing universality of neural nets (revisited)_ showed that the elements (axioms) of partial recursive functions may be computed by an RNN. However, this only shows that a Turing complete RNN exists (similar to previous work) based on the fact that the elements needed to implement any partial recursive function are present and a Turing machine is a partial recursive function based on the fact that the class of functions which are Turing computable is equivalent to the class of partial recursive functions and a Turing machine can simulate any other Turing machine (therefore it iself belongs to the class of partial recursive functions). The point in this paper is that such a Turing complete RNN must have a latent output sequence. The latent output sequence may be embedded in the main output, however differentiation between final output and latent calculations is necessary for the output to be interpretable. 


