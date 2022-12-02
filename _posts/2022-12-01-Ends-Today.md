## It Ends Today

Today is the culminating project presentation for my capstone 2 students. So, a good deal of work for me happens next week in grading them. However, in the short term this gives me some additional time. 

## Today

My goal is to work with the GPT interface for 1 hour and write on my game theory paper for 1 hour. I have already asked for subsidized access to the GPT-3 API and am waiting on open-AI to respond. 

When those tasks are done, I will follow up with my collaborator on the ASEE papers.

## GPT-3 Chiasm Detection via Few Shot Learning

The following results were obtained via few shot learning and the GPT-3 playground:

Few shot training:

> ban with permit reservation to a permit with ban is a chiasm.
> citizen consumers rather than consumer citizens is a chiasm.
> Independence is language and language is independence is a chiasm.
>
> rules and laws and that laws and rules is not a chiasm.
> Directive is inapplicable in Denmark , or Denmark is required by the Directive is not a chiasm.

testing: 

> man is not made for the law , but rather law is made for man is a chiasm.
>
> tabled amendments , that is , amendments tabled is not a chiasm.

The above testing was done by hand. So, the number of items used to test were small. However, this does give reason to believe that the model may already have an internal representation that is more than suitable to desegregate chiasma from non-chiasma. 

### Details of the above

    response = openai.Completion.create(
      model="text-davinci-003",
      prompt="",
      temperature=0,
      max_tokens=6,
      top_p=1,
      frequency_penalty=0,
      presence_penalty=0,
      stop=["\n"]
    )

The prompt value was all words up to and including the final instance of the token "is" in each of the testing statements. 

#### Few shot training methodology

The few shot learning method employed is based on converting the task to a cloze task (complete the sentence or fill in the blank). However, to do this it is helpful to provide the language model a hint as to how it should respond. The hint can be effectively provided in the form of an established pattern. 

This method bears a coincidental resemblance to the method discussed here:
##### Exploiting Cloze Questions for Few Shot Text Classification and Natural Language Inference

There are some very recent methods to perform few shot learning with fine tuning based on an idea called adapters. The notion of an adaptor is that a small set of parameters (like an additional fully connected layer) could be randomly initialized and inserted. These weights are then the only degrees of freedom in the network when it is finetuned. 

##### Parameter-efficient transfer learning for nlp

The adapters suggested above and used for tuning a network should also be able to learn to *embed additional information* which may vary at frequencies different from typical tokens (like author information?). Further, combining this with the paper on [identifying counterfactual edits in PLMs](https://jessetnroberts.github.io/2022/11/15/The-Shed.html) could yield a good method to add information at the proper layer in a transformer language model.  

##### PERFECT: Prompt-free and Efficient Few-shot Learning with Language Models



## Scale it up

The first thing that I need to do is to scale up the experiment in such a way that the results from past work can be compared. I think it best to run a comprehensive experiment and then log the data for analysis. 

However, I suppose this presents a bit of an issue as I'm not certain how few shot learning is evaluated. It makes some sense that it would be evaluated as usual with a form of cross validation. But that will require a great many api calls, which... I don't have access to.

### Side note: Does anyone else see an issue with N-fold cross validation?

Also, in general cross validation is an odd concept as it penalizes the reality that some data makes for better training than other data. The purpose of n-fold cross validation is to avoid having a training or test set that causes good results that are unlikely or unrepeatable. However, training data needs to sufficiently bound and define the space, otherwise it is insufficient training. 

Obviously, data leakage (data that is present in the test set and the training set) is a major issue in ML. However, N-Fold cross validation seems like it may be more a measure of the nature of the distribution of the data and bias of the network. 

Consider that neural networks have a bias toward certain data distributions based on architecture and initial weighting. Then some data will inherently have a statistical structure that is more congruent with the bias of the network. These will be more easily learned by the network. So, having a network that easily learns from any subset of data from the overall distribution suggests that the network's bias matches the data's structure. 

That's not very important. In education it is often the case that curated examples are necessary to clearly define a concept. Real issues like memorization (overfitting) and data leakage shouldn't lead to bad validation practices. 

It is theoretically true that given a network and a set of data, there is some optimal finite training subset that will facilitate generalization better than any other finite subset on the total space of possible samples. The use of such a subset for training does not necessary conote any data leakage or overfitting. 

If it were possible to identify such a subset, then it would seem appropriat to distribute the training exemplar set with the network. 

### How are few shot learning systems typically evaluated?






