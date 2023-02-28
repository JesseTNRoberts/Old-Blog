## Breadth reading in Computational Linguistics


### Adversarial Stylometry in the Wild: Transferable Lexical Substitution Attacks on Author Profiling


In this paper the authors are obfuscating certain information about a target which may be inferrable given word choices in a document written by the author. In lieu of access to test subjects as classifiers, they train a simple gender classifier and then try to learn an obfuscation adversarially. Specifically, they identify the tokens which most correlate with the target author's gender based on the classifier. Then, they substitute these words with BERT through masking. 

- (Idea) First, the method used to assign gender predictability (or any label predictability) is a bit coarse. CLMs could be finetuned to classify the gender (or any label). Then, the attention vector when infering the label should be indicative of the tokens in situo which contribute most significantly.  

- (Idea) Second, generating the replacement words with BERT is probably not a great choice. The authors correctly identify that BERT will not prevent semantic drift as words are replaced. To avoid this, an encoder/decoder model should be used (to reduce semantic drift).


