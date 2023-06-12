## Main Problems with Current Transformers

For each of the items below, two natural questions emerge. 

*How can existing transformer based language models be used so that they may perform these?*
*How can the transformer architecture be improved to perform these?*


### Computation

- Deliberation

Based on my own work, transformer language models are not Turing complete as it is impossible for a transformer (among others) to simulataneously be employed as a sequence-to-sequence model and be Turing complete. Adding a memory module, changing to hard attention with infinite precision, or having infinite length output won't solve this issue.

The solution must decouple not only the computational storage location but the number of computations from the output.

There is evidence that suggests this could significantly improve the multistep reasoning of transformers. CoT. 

It seems that an additional "tape" would solve this issue. Two tape transformers! With internal and external dialogues! I bet there is good theoretical backing for this. I bet a 2 tape B machine is capable of generating the tape of an arbitrary Turing machine. 

### Attention Strategies

- Myopic Attention

Based on Hahn's Lemma, the theoretical maximum contribution of any single token the output of the network is $1/n$.


- Hyperopic Attention

Currently, hyperopic attention is imfeasible for transformers as the length of the context grows, the number of parameters tends to grow quadratically. 



### Plan Driven Sub-Space Sampling of a Language Model

- Planning

Absent a greater discourse or narrative, any substring may be completed in infinitely many ways as there are infinitely many discourses in which the substring may lie. How can the planned discourse or narrative be used to shape the probability space of the completion? 

As an example, the authors of (ExpertPrompting: Instructing Large Language Models to be Distinguished Experts) develop a prompting scheme such that the probability space is biased to sound as if it is an expert. This dramatically changes the completion quality. 

Obviously, this suggests that prompting is a viable method. However, this requires that we have a suitable prompt that captures the relevant discourse information to shift the probability space.

Another method may be to expand the subtree of the narrative/discourse and then prune elements from the tree that deviate from the plan to a degree that makes the plan impossible. 

Perhaps one method of this would be to generate a static plan a priori, then use the plan to prompt the model. At each point, the real current state would be the result of the last generation and at each generation step the model would be encouraged to generate a story that went from the current state to the target state. However, in many situations, the target state may be unreachable (whether to a large extent or small). Therefore, the actual next state may be off path by some small amount. Therefore, the realized narrative/discourse may deviate from the path but ultimately achieve the goal. 

