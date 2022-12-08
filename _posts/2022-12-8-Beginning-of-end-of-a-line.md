## Finish it: The Traveler's Dilemma

The traveler's dilemma is an interesting strategic scenario because it is a paradoxical game. It possesses a unique situation in which the players may actually obtain a better payoff if they do not act in accord with typical notions of rationality. Namely, they get a better outcome by ignoring the Nash equilibrium. 

However, I have found a compelling explanation for the phenomena which stems from computational considerations. The paradox exists because the game theoretic analysis is conducted without considering the impact of computational time and the underlying algorithm. 

The typical analysis in game theory makes 2 key (but unintentional) assumptions. First, it assumes that the agents have infinite computational time and space. Second, it assumes that agents' algorithmic selection of a strategy happens at the end of execution. 

When these assumptions are made explicit, they may be relaxed to evaluate the effect on the predicted equilibrium. Importantly, when computational time and space is no longer assumed infinite, and it is allowed that the agent themselves may be uncertain of afforded computational time, it is no longer tenable to assume that a preference algorithm would only provide output upon completion of execution. Rather, the algorithm would provide a continually updated best strategy.  

The result is that stochastic computational space and time may cause agents to terminate before the algorithm converges.


## Hypothesis 1

This leads to the first hypothesis. In the interest of disambiguation, the claim *is not* if infinite time is given to a player, the Nash equilibrium will be selected. The hypothesis is that if a set of players had developed in societies with infinite and deterministic computational resources then those players would select the Nash equilibrium. 

In the natural world, that is not the case. Humans (and strategic players in general) have limited computational resources and often have limited predictability regarding allocation. Therefore, they have optimized expectations of opponents based on these conditions. 


## Abstract Strategies: Meta Learning in Game Theory

One way of understanding this is to consider that the idea of rationality for humans is specific to the context. That is, it would be irrational to have a method of choosing which was not sensitive to the computational context. Then, when expecting an opponent's actions, the method of choice optimized for the computational context should be imputed to the opponent (assuming no explicit contradictory information is possessed).  

However, a potentially equivalent perspective is that humans are engaged in evolutionary game theory with abstract or meta strategies being the things which are learned rather than strategies. Evolutionary game theory shouldn't typically apply to the traveler's dilemma as it is a one shot game. If humans do not learn strategies and instead learn meta strategies, this contention is resolved. 


## Hypothesis 2

If game theory experts were to be asked to choose a strategy in the traveler's dilemma but were told that their opponent was a computer they may choose the Nash equilibrium strategy. The reason is because they may not have a bias toward expecting the opponent to think like themselves.


## Hypothesis 3 

Focal Points may be understood as the first output from the choice algorithm. 

### Prediction 3.1

From the above hypothesis, we may limit the computational resources by constraining the time or the space, either of which should adversely effect the algorithms execution. In contexts which bias the player toward progressive search (like visual search problems tend to) it is likely that constraining the computational resources may cause the selected strategies to tend toward the focal point.   

Time constraint has been experimentally evaluated in previous work and has proven that in the face of time constraints humans tend toward focal points in visual search. However, similar experimentation has not been conducted in the case of the traveler's dilemma. It is predicted that limiting the time to choose should push players toward 100 (the most obvious focal point).

### Prediction 3.2

As an extension of the above, it is predicted that limiting the computational space by asking players to remember a number of items (which if forgotten cause the reward to be zero) while performing visual search is likely to cause players to tend toward focal points. 



