# Text Preprocessing in Python1

Whenever we have textual data, we need to apply several pre-processing steps to the data to transform words into numerical features that work with machine learning algorithms.

```
# import the necessary libraries
import nltk
import string
import re
```

**Text Lowercase:**
We lowercase the text to reduce the size of the vocabulary of our text data.

```
def text_lowercase(text):
	return text.lower()

input_str = "Hey, did you know that the summer break is coming? Amazing right !! It's only 5 more days !!"
text_lowercase(input_str)
```

**Remove numbers:**
We can either remove numbers or convert the numbers into their textual representations.
We can use regular expressions to remove the numbers.
```
# Remove numbers
def remove_numbers(text):
	result = re.sub(r'\d+', '', text)
	return result

input_str = "There are 3 balls in this bag, and 12 in the other one."
remove_numbers(input_str)
```

**Example:**

    Input: “There are 3 balls in this bag, and 12 in the other one.”
    Output: ‘There are balls in this bag, and in the other one.’

**Remove punctuation:**
We remove punctuations so that we don’t have different forms of the same word.
```
# remove punctuation
def remove_punctuation(text):
	translator = str.maketrans('', '', string.punctuation)
	return text.translate(translator)

input_str = "Hey, did you know that the summer break is coming? Amazing right !! It's only 5 more days !!"
remove_punctuation(input_str)
```

**Remove whitespaces:**
We can use the join and split function to remove all the white spaces in a string.
```
# remove whitespace from text
def remove_whitespace(text):
	return " ".join(text.split())

input_str = " we don't need the given questions"
remove_whitespace(input_str)
```

**Remove default stopwords:**
Stopwords are words that do not contribute to the meaning of a sentence. Hence, they can safely be removed without causing any change in the meaning of the sentence. 

<img src="https://media.geeksforgeeks.org/wp-content/uploads/20190524004259/Screenshot-1053.png">

```
from nltk.corpus import stopwords
from nltk.tokenize import word_tokenize

# remove stopwords function
def remove_stopwords(text):
	stop_words = set(stopwords.words("english"))
	word_tokens = word_tokenize(text)
	filtered_text = [word for word in word_tokens if word not in stop_words]
	return filtered_text

example_text = "This is a sample sentence and we are going to remove the stopwords from this."
remove_stopwords(example_text)
```

**Example:**

    Input: “This is a sample sentence and we are going to remove the stopwords from this”
    Output: [‘This’, ‘sample’, ‘sentence’, ‘going’, ‘remove’, ‘stopwords’]

**Stemming:**
Stemming is the process of getting the root form of a word. Stem or root is the part to which inflectional affixes (-ed, -ize, -de, -s, etc.) are added. The stem of a word is created by removing the prefix or suffix of a word. So, stemming a word may not result in actual words.