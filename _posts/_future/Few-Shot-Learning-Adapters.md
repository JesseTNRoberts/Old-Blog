## Where should Adapters be inserted?

There are some very recent methods to perform few shot learning with fine tuning based on an idea called adapters. The notion of an adaptor is that a small set of parameters (like an additional fully connected layer) could be randomly initialized and inserted. These weights are then the only degrees of freedom in the network when it is finetuned. 

#### Parameter-efficient transfer learning for nlp

While reading about the adapters used to do few shot fine tuning in pretrained language models it struck me that they should have an optimal insertion in the same way that there are optimal edits to networks to create factual edits in the network. 

The adapters suggested above and used for tuning a network should also be able to learn to *embed additional information* which may vary at frequencies different from typical tokens (like author information?). Further, combining this with the paper on [identifying counterfactual edits in PLMs](https://jessetnroberts.github.io/2022/11/15/The-Shed.html) could yield a good method to add information at the proper layer in a transformer language model.  

#### PERFECT: Prompt-free and Efficient Few-shot Learning with Language Models
