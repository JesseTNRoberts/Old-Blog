# Introductions

I've been researching for a while. I have some publications. But now I need to develop and finish my dissertation. 

So, with no more introduction...

## Today in my head

I'm working on finishing a paper about uncertainty in game theory and looking into author information in language models. Also, in the background I'm watching "Honor Society".

I won't say too much about the paper (Because that would be boring). However, I'll talk about the papers I explore and comment on the movie.

## Language models and authors

Language models (ok, specifically I'm refering to transformer based models) are powerful tools that have been used somewhat successfully to do zero shot learning. That's pretty cool. 

Language models take in sequential information in the form of words. But the general architecture is known as a sequence to sequence model. That is a model that takes in a sequence and produces a sequence. This means that they aren't actually limited to words. Rather, any sequential information is fair game.

If you think about words, they are a rather fast changing signal, while other NLP signals change more slowly. Namely, I'm thinking about the author, but other signals are also slow moving (topic, time period, etc). However, large language models like GPT-x don't encode tokens capturing any of these slower moving signals. 

You could retrain the model to include additional tokens. But end to end incorporation of additional tokens would take too much computational time/space. 

## Honor Society; or, a waste of time

Honor Society is a fine movie. It starts as an offbeat sort of sociopath out of water story. This is promising. I rooted for Honor to follow thorugh on her annihilation of competitors for the Harvard recommendation. Instead it takes a predictable and silly turn. Won't spoil it.. but it plays as if the writer didn't have the stomach to follow through on the cold, hard facts of life promise. Instead, near the end they got nervous the audience wouldn't be onboard and went with "jk! she's a normal teen girl".

I'm switching to Seinfeld.

## Question - Do language models implicitly learn information about the author and style?

My guess is this has been addressed in some fashion before. I am aware of GPT-2 based zero shot trivia tasks (presented in the Open AI paper introducing GPT-2). But, I'm guessing that GPT-2 won't be able to identify the author of common quotes. I also bet that GPT-2 won't be able to predict the author given something written in a stereotypical style. 

However, based on older research, I'm going to guess that pretrained models do have internal representations that could be used to the identify slower moving characteristics. 

But let's see what's out there now..


#### TweepFake: About detecting deepfake tweets

This paper is related if you limit the space of possible authors to human and not-human. 

They reference work done by GPT-2 engineers in which texts were labeled as human and non-human using zero shot learning. If the text was closer based on likelihood to machine recommended (I assume GPT-2 specifically) texts than human texts, then it was labeled as non-human. I'm not sure this is helpful.

In general though, this paper says that RNN based models are better suited to classify the author of a tweet (in a binary author context) than larger language models based on their experiments. They theorize this may be because tweets don't need language model long range relationship representations. RNNs may be more appropriate in short text author identification.  

##### Relevant Takeaway

So, the language models probably encode representations that are *rich enough* to predict things about the author. Otherwise, the LM based methods wouldn't have been able to predict machine or human author. 


#### Enough for the first day of blogging

This was a fairly successful method of blogging. Little effort is needed to make a post and enter the information. I think I'll stick with it.

Since I am also remodeling the house and teaching full time, some posts may be about house remodels or teaching instead of research. However, my target is to post three times a week on research.










