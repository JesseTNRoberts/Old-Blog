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

## Honor Society; or, A waste of time

Honor Society is a fine movie. It starts as an offbeat sort of sociopath out of water story. This is promising. I rooted for Honor to follow thorugh on her annihilation of competitors for the Harvard recommendation. Instead it takes a predictable and silly turn. Won't spoil it.. but it plays as if the writer didn't have the stomach to follow through on the cold, hard facts of life promise. Instead, near the end they got nervous the audience wouldn't be onboard and went with "jk! she's a normal teen girl".


## Question - Do language models implicitly learn information about the author and style?

My guess is this has been addressed in some fashion before. I am aware of GPT-2 based zero shot trivia tasks (presented in the Open AI paper introducing GPT-2). Moreover, I am guessing that GPT-2 won't be able to identify the author of common quotes. I also bet that GPT-2 won't be able to predict the author given something written in a stereotypical style. But let's see what's out there now..








