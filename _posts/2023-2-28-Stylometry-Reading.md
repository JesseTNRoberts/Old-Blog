## Breadth reading in Computational Linguistics


### Adversarial Stylometry in the Wild: Transferable Lexical Substitution Attacks on Author Profiling


In this paper the authors are obfuscating certain information about a target which may be inferrable given word choices in a document written by the author. In lieu of access to test subjects as classifiers, they train a simple gender classifier and then try to learn an obfuscation adversarially. Specifically, they identify the tokens which most correlate with the target author's gender based on the classifier. Then, they substitute these words with BERT through masking. 

The goal is to fool humans such that (1) the semantic meaning is maintained, (2) the authors private information is obfuscated such that a classifier has no better than chance (or potentially negative correlation unless opposite label bias is also to be avoided) accuracy, and (3) humans can't identify the obfuscated tokens.

- (Idea) First, the method used to assign gender predictability (or any label predictability) is a bit coarse. CLMs could be finetuned to classify the gender (or any label). Then, the attention vector when infering the label should be indicative of the tokens in situo which contribute most significantly.  

- (Idea) Second, generating the replacement words with BERT is probably not a great choice. The authors correctly identify that BERT will not prevent semantic drift as words are replaced. To avoid this, an encoder/decoder model should be used (to reduce semantic drift).

- (Idea) The previous two ideas are combined in a feedback system so that the model obfuscates until prediction drops to the desired level. Then a task specific classifier is used to validate the model.


### The Limitations of Stylometry for Detecting Machine-Generated Fake News

Interesting but somewhat outdated paper in which the authors show that machine generated text can be detected through stylometry. Stylometry is also somewhat effective at detecting human generated fake news. However, transformer based, human in the loop generation of fake news can't be discerned stylometrically from legitimate content. They theorize that the cause is a lack of bias coming from a lack of hidden awareness of falsity (my words not theirs - but their concept).


### Detecting Individual Decision-Making Style: Exploring Behavioral Stylometry in Chess

In this paper the authors build an architecture which includes a transformer module. Specifically, they use CNNs to perform feature extraction, then they use positional embeddings so that time information is captured. Then, it is passed to a transformer. The architecture is encoder only (though I'm not clear on what embedding they are using precisely - it seems to be learned). The logit outputs are used through averaging to generate the classification. 

The authors attempt to evaluate the moves in the game which are (based on attention) most informative to player identity. They conclude that the earlier moves are most important as the attention to moves drops more or less linearly with order. 

They did not pretrain the transformer to predict missing moves. So, they took a denoising architecture and did not apply the appropriate method of training. I believe the attention analysis should have been a strong indication that something is not workin the way it should. 

- (question) The interesting question is, if we reject inherent importance of opening moves (which should be rejected as this trend was maintained even when the actual first moves were dropped), why does it seem that the transformer attention tends to focus on the inputs which occur at the beginning of the sequence. 

I tend to think this must have something to do with the math of the transformer. And it begs the question, is it true in other problems with other feature embeddings?




