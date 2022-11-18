## The Chiasm 

Chiasmi are literary structures commonly found in ancient Greek writing. They are considered a structural form in classical rhetorical writing. These forms (generally) exist as a product of intention on the part of the author. Identifying and studying these forms is of significant interest to many research communities including philology, linguistics, rhetorics, and theology. 

### Machine Learning for Rhetorical Figure Detection: More Chiasmus with Less Annotation - 2017

This paper and a few others by the same two authors are the only people addressing this question. The authors are both from a linguistics and philology background. 

The paper applies simple, older language models to label and find the structures based on token repetition and mutual order. Then they rank the retrieved instances based on a loose notion of probability. 

#### Relevant Takeaway

No-one has addressed this with transformer based language models. The literature search did not yield any attempts at generating chiasmi either. 


### It starts to sound promising

Evaluate the ability of transformer based language model(s) to identify and generate chiasmi. 

#### Is it doable?

These language models have selective attention. They may not be able to identify chiasmi in a zero shot context (as rhetorical forms are not commonly called out in modern text). But! I hypothesize that (a) a LM possesses sufficient representational power to capture chiasmus structure, (b) has an ideal approach to capturing the structure (multi-resolution self-attention), and (c) may be able to learn to generate (and thus internalize the concept) with simple prompt programming. 

#### What about data?

The authors mentioned above have a link to a dataset they curated which contains true, borderline, and false chiasmi. The dataset can be found [here](http://stp.lingfil.uu.se/~marie/chiasme.htm). I'm going to download the dataset and add it to a github repo [here](https://github.com/JesseTNRoberts/ChiasmNLP/tree/main/Data) to ensure I have it when I need it. 

Thanks for the dataset! If it weren't for people like the authors of the above paper, who are doing foundational research in the field of linguistics, computer scientists like me (not a linguist) couldn't contribute!

#### Let's be specific 

I have identified a high level task, a hypothesis, and data. Now all I need is a method. 

What I have in mind is
- use prompt programming on GPT-3 to establish chiasm conceptual understanding in the GPT-3 pretrained model.
- use fine tuning on BERT or GPT-2 to bias the pretrained model toward chiasm generation.
- add an output layer and train GPT-2 or BERT end-to-end for 1 to 3 epochs to classify text as containing or not containing a chiasm.

#### Running the experiments

Record scratch. Pause that thought. Because even though I have everything I need. GPT-3 is no longer the flagship language model from openAI. So, for the first experiment mentioned, I may need to move to their latest model. I will have to read the new paper to know.

### But first, we feast

Ran to get some groceries and lunch. I have decided to watch more closely what I am eating and have been using Lose it as a calorie and nutrient counter. I might start adding my meals to my daily post. Maybe, that might be distracting.

Anyway, Garfield Thanksgiving and lunch done. Back to it.

### Training language models to follow instructions with human feedback - 2022

The punchline is already given away. OpenAI has generated a newer language model called instructGPT. Apparently they layered on reinforcement learning to help the pretrained GPT-3 learn things that weren't helpful to say.

An interesting note from the blurb on OpenAI's webpage says that instructGPT tends to "make up facts less often". That is interesting because the notion of making up a fact is an anthropomorphization. GPT-x does not make up facts. Based on the paper I talk about [here](https://jessetnroberts.github.io/2022/11/15/The-Shed.html) it seems that facts are just values selected by keys at a previous layer in the model. So, editing a fact is as simple as editing the right weights. However, they point out that this causes the language model to simply select another value from the abstracted part of speech. If this is the case, how can instructGPT prevent this? 

Looking into it a bit more, it seems that the comment regarding making things up has more to do with closed domain questions (those where you answer questions about a passage). Then if a model introduces new (madeup) information, it is said to have hallucinated. 

Anyway, that's interesting and all. But what I wanted to know is if I should use instructGPT or GPT-3. However, the OpenAI API has both available. So, it seems prudent to try chiasm generation on both. 

Question answered. 

#### Relevant Takeaway

InstructGPT seems to be more "aligned" the user base of openAI. The jury is still out on whether this will yield a better system for research. But it is certainly a better commercial product.

### To class

Capstone 2 is coming to an end very quickly. I am intensely proud of both teams. But I do feel that I have not been as present in capstone 2 as I would like. Formalizing and overseeing capstone 1 takes a significant amount of time. 

However, at the end of the day, I have given them everything they need to succeed. It is up to them what they do with it. 



