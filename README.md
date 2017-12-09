# aquila

## Development scripts
To run a common development script, execute one of the following commands:
- `sudo pip3 install -r requirements.txt`: Installs dependencies and dev dependencies.
- `python3 -m unittest discover -s .`: Launches the test runner running all tests.

## Question 1
Below are some of my open source projects.

### elephant
- project URL: https://github.com/yuchenhou/elephant
- feature description: https://github.com/yuchenhou/elephant/blob/master/predict_link_weight.feature
- project type: deep learning

### rat
- project URL: https://github.com/yuchenhou/rat
- feature description: https://github.com/yuchenhou/rat/blob/master/classify_dna.feature
- project type: deep learning

### ajobpool
- project URL: https://gitlab.com/alanhou/ajobpool
- demo site URL: https://gitlab.com/alanhou/ajobpool
- project type: progressive web application

###### notes
- I did not include any Ruby project because I haven't used Ruby in 5 years.
But I am happy to get better at Ruby if your team uses Ruby for your projects.
- I included a Javascript project because I assume your team uses Javascript
for frontend web development and I think it is relevant skill.

## Question 2
The solution to this problem consists of the following steps:
- Extract the company name
- Lookup the company industry

Neither of these steps is simple.
Below is an over view of each step.

#### Extract the company name
In this stage, the program extracts the name of the company from the transaction text description.

A naive solution is to reduce this problem to the Name Entity Recognition problem,
and apply a Named Entity Recognizer(NER).
A popular implementation of NER is the Stanford NER: https://nlp.stanford.edu/software/CRF-NER.shtml .
Stanford NER has a Python interface in python package NLTK: http://www.nltk.org/api/nltk.tag.html#module-nltk.tag.stanford .
NERs perform very well written English text data.
Unfortunately, they don't perform well in informal, short, incomplete sentences, such as transaction description:
https://www.quora.com/How-can-I-find-city-country-company-name-from-a-tweet-text-using-Java/answer/Jasneet-Sabharwal
because transaction descriptions lack of the structures in complete sentences.

An alternative solution is to apply a part-of-speech tagger trained on informal and short sentences such as
Tweet NLP: http://www.cs.cmu.edu/~ark/TweetNLP/ .

If neither of these solution has good enough performance on transaction text description,
a dedicated recognizer or tagger trained on transaction text description data is a potential solution

#### Lookup the company industry
In this stage, the program looks up the company industry
by calling a company information lookup API with the company name.
This API can be provided by a third party or in house.
To build a in house service for this task,
we can collect company information (name and industry) through an API provided by
a popular social network such as uch as Linkedin, Facebook,
and store the data in a database.

## Question 3

#### Add a test case
To add a test case for a new transaction,
locate the list `transactions`
in `test_question3.TestQuestion3.test_has_word_aquila()`,
add a new dictionary for the new transaction in it
including the `text` field and the `expected_label` field.
