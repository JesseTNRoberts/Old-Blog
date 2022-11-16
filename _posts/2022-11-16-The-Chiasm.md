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



