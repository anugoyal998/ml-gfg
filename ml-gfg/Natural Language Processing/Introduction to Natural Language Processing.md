# Introduction to Natural Language Processing

**creating an NLP pipeline**

`Step #1: Sentence Segmentation`
Breaking the piece of text in various sentences.

    Input : San Pedro is a town on the southern part of the island of Ambergris Caye in the Belize District of the nation of Belize, in Central America. According to 2015 mid-year estimates, the town has a population of about 16, 444. It is the second-largest town in the Belize District and largest in the Belize Rural South constituency.

    Output : San Pedro is a town on the southern part of the island of Ambergris Caye in the 2.Belize District of the nation of Belize, in Central America.
    According to 2015 mid-year estimates, the town has a population of about 16, 444.
    It is the second-largest town in the Belize District and largest in the Belize Rural South constituency.
    For coding a sentence segmentation model, we can consider splitting a sentence when it encounters any punctuation mark. But modern NLP pipelines have techniques to split even if the document isn’t formatted properly.

`Step #2: Word Tokenization`
Breaking the sentence into individual words called as tokens. We can tokenize them whenever we encounter a space, we can train a model in that way. Even punctuations are considered as individual tokens as they have some meaning.

    Input : San Pedro is a town on the southern part of the island of Ambergris Caye in the Belize District of the nation of Belize, in Central America. According to 2015 mid-year estimates, the town has a population of about 16, 444. It is the second-largest town in the Belize District and largest in the Belize Rural South constituency.

    Output : ‘San Pedro’, ’ is’, ’a’, ’town’ and so.

`Step #3: Predicting Parts of Speech for each token`
Predicting whether the word is a noun, verb, adjective, adverb, pronoun, etc. This will help to understand what the sentence is talking about. This can be achieved by feeding the tokens( and the words around it) to a pre-trained part-of-speech classification model. This model was fed a lot of English words with various parts of speech tagged to them so that it classifies the similar words it encounters in future in various parts of speech. Again, the models don’t really understand the ‘sense’ of the words, it just classifies them on the basis of its previous experience. It’s pure statistics.

`Step #4: Lemmatization`
Feeding the model with the root word.
For example –

    There’s a Buffalo grazing in the field. 
    There are Buffaloes grazing in the field. 

Here, both Buffalo and Buffaloes mean the same. But, the computer can confuse it as two different terms as it doesn’t know anything. 

`Step #5: Identifying stop words`
There are various words in the English language that are used very frequently like ‘a’, ‘and’, ‘the’ etc. These words make a lot of noise while doing statistical analysis. We can take these words out. Some NLP pipelines will categorize these words as stop words, they will be filtered out while doing some statistical analysis.

`Step 6.1: Dependency Parsing`
This means finding out the relationship between the words in the sentence and how they are related to each other. We create a parse tree in dependency parsing, with root as the main verb in the sentence. If we talk about the first sentence in our example, then ‘is’ is the main verb and it will be the root of the parse tree. We can construct a parse tree of every sentence with one root word(main verb) associated with it. We can also identify the kind of relationship that exists between the two words. In our example, ‘San Pedro’ is the subject and ‘island’ is the attribute. Thus, the relationship between ‘San Pedro’ and ‘is’, and ‘island’ and ‘is’ can be established.

Just like we trained a Machine Learning model to identify various parts of speech, we can train a model to identify the dependency between words by feeding many words. It’s a complex task though. In 2016, Google released a new dependency parser Parsey McParseface which used a deep learning approach.

