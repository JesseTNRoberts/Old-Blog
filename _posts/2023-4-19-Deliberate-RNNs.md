## Deliberate RNNs

To restore the Turing completeness result for RNNs it is necessary to change the method by which they are applied as shown in previous work. A concrete method to restore this is described below. 

Using dropout we are able to get a measure of the certainty of a neural network. We may define an input to the network as the latch input. While this is high, the network should deliberate on the appropriate output. That is, the network should attempt to hold the output stable while the input is high. However, to do so, it will need to fight against the noise induced by randomized dropout. The output considered to be the final decision of the network is the output after a number $k$ of stable epochs during which the output changes by no more than $\epsilon$. 

In this manner the network will learn to use its last output to deliberate and come to a stable output. Stability is interpreted as certainty. By allowing deliberation to be unbounded in number of epochs, the network is capable of unbounded minimization. Therefore, the Turing completeness result is restored. 

An interesting question is, which is better, a predefined $k$ or a stochastic value of required stable epochs? 


