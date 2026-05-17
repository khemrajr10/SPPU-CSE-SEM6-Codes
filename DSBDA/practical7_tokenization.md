Practical7_TextAnalysis

1. Extract Sample document and apply following document preprocessing methods: 
Tokenization, POS Tagging, stop words removal, Stemming and Lemmatization. 
2. Create representation of document by calculating Term Frequency and Inverse Document 
Frequency. 

Code:

import nltk
import pandas as pd

from nltk.tokenize import word_tokenize
from nltk.corpus import stopwords
from nltk.stem import PorterStemmer
from nltk.stem import WordNetLemmatizer
from nltk import pos_tag

from sklearn.feature_extraction.text import TfidfVectorizer

# Download Required Resources
nltk.download('punkt')
nltk.download('punkt_tab')
nltk.download('stopwords')
nltk.download('averaged_perceptron_tagger')
nltk.download('averaged_perceptron_tagger_eng')
nltk.download('wordnet')

# Sample Document
document = """
Text Analytics is the process of converting unstructured text data
into meaningful information. Natural Language Processing helps
machines understand human language.
"""

# Tokenization
tokens = word_tokenize(document)

print("TOKENS")
print(tokens)

# POS Tagging
pos_tags = pos_tag(tokens)

print("\nPOS TAGS")
print(pos_tags)

# Stop Words Removal
stop_words = set(stopwords.words('english'))

filtered_tokens = []

for word in tokens:

    if word.lower() not in stop_words:

        filtered_tokens.append(word)

print("\nAFTER STOP WORD REMOVAL")
print(filtered_tokens)

# Stemming
stemmer = PorterStemmer()

stemmed_words = []

for word in filtered_tokens:

    stemmed_words.append(stemmer.stem(word))

print("\nSTEMMED WORDS")
print(stemmed_words)

# Lemmatization
lemmatizer = WordNetLemmatizer()

lemmatized_words = []

for word in filtered_tokens:

    lemmatized_words.append(
        lemmatizer.lemmatize(word)
    )

print("\nLEMMATIZED WORDS")
print(lemmatized_words)

# TF-IDF Representation
documents = [

    "Text Analytics converts text into information",

    "Natural Language Processing helps understand language",

    "Text mining and NLP are important in analytics"
]

tfidf = TfidfVectorizer()

tfidf_matrix = tfidf.fit_transform(documents)

tfidf_df = pd.DataFrame(
    tfidf_matrix.toarray(),
    columns=tfidf.get_feature_names_out()
)

print("\nTF-IDF REPRESENTATION")
tfidf_df

Explanation:
1. What is the objective of this practical?

The objective of this practical is to perform text preprocessing operations and create document representation using TF-IDF in Text Analytics.

2. What is Text Analytics?

Text Analytics is the process of converting unstructured text data into meaningful information using NLP techniques.

3. What is NLP?

Natural Language Processing is a branch of AI that helps computers understand and process human language.

4. Which libraries are used in this practical?
Library	Purpose
NLTK	NLP preprocessing
pandas	Data handling
scikit-learn	TF-IDF calculation
5. Why did you import NLTK?

NLTK provides NLP tools such as:

tokenization
stop words
POS tagging
stemming
lemmatization
6. What is the purpose of downloading NLTK resources?
nltk.download()

downloads required NLP datasets and tokenizers.

7. Why is punkt downloaded?
nltk.download('punkt')

Punkt tokenizer is used for tokenization.

8. Why is stopwords downloaded?
nltk.download('stopwords')

It provides predefined stop words list.

9. Why is averaged_perceptron_tagger downloaded?
nltk.download('averaged_perceptron_tagger')

It is used for POS tagging.

10. Why is wordnet downloaded?
nltk.download('wordnet')

WordNet dictionary is required for lemmatization.

11. What is a document in Text Analytics?

A document is a collection of text used for NLP processing.

Example:

paragraph
article
sentence
12. What is sample document in your code?
document = """ ... """

It contains sample text for preprocessing operations.

13. What is Tokenization?

Tokenization is the process of breaking text into smaller units called tokens.

14. How did you perform tokenization?
tokens = word_tokenize(document)

This splits document into words and punctuation marks.

15. Example of tokenization

Input:

"Text Analytics is useful."

Output:

['Text', 'Analytics', 'is', 'useful', '.']
16. What are tokens?

Tokens are individual words, symbols, or punctuation obtained after tokenization.

17. What is POS Tagging?

POS means:

Parts Of Speech

POS tagging identifies grammatical role of words.

Example:

noun
verb
adjective
18. How did you perform POS Tagging?
pos_tags = pos_tag(tokens)
19. Example of POS Tagging

Output:

('Text', 'NN')

Meaning:

Text → Noun
20. Common POS Tags
Tag	Meaning
NN	Noun
VB	Verb
JJ	Adjective
RB	Adverb
21. What are Stop Words?

Stop words are commonly used words that carry little meaning.

Examples:

is
the
and
into
22. Why are stop words removed?

Because they:

increase processing
do not contribute much meaning
23. How did you remove stop words?
stop_words = set(stopwords.words('english'))

Then words are filtered using loop.

24. Explain this code.
if word.lower() not in stop_words:

Checks whether word is NOT a stop word.

25. What is Stemming?

Stemming reduces words to root/base form by removing suffixes.

26. How did you perform stemming?
stemmer = PorterStemmer()
stemmer.stem(word)
27. Example of stemming
Original Word	Stemmed Word
playing	play
converting	convert
studies	studi
28. What is Lemmatization?

Lemmatization converts words into meaningful dictionary base form.

29. Difference between stemming and lemmatization?
Stemming	Lemmatization
Removes suffixes	Uses dictionary meaning
May produce invalid words	Produces valid words
Faster	More accurate
30. How did you perform lemmatization?
lemmatizer = WordNetLemmatizer()
lemmatizer.lemmatize(word)
31. Example of lemmatization
Original Word	Lemmatized Word
studies	study
better	good
running	run
32. What is document representation?

Document representation converts text into numerical format understandable by machine learning models.

33. What is TF-IDF?

TF-IDF stands for:

Term Frequency - Inverse Document Frequency

It measures importance of a word in a document.

34. What is Term Frequency (TF)?

TF measures how frequently a word appears in a document.

Formula:

TF = Number of times term appears / Total words
35. What is Inverse Document Frequency (IDF)?

IDF measures importance of a word across multiple documents.

Formula:

IDF = log(Total Documents / Documents containing term)
36. Why is TF-IDF used?

TF-IDF gives higher importance to meaningful words and lower importance to common words.

37. How did you create TF-IDF representation?
tfidf = TfidfVectorizer()
38. Explain this code.
tfidf_matrix = tfidf.fit_transform(documents)
fit() learns vocabulary
transform() converts documents into TF-IDF matrix
39. Why multiple documents are used?

TF-IDF compares words across multiple documents to calculate importance.

40. What is TF-IDF matrix?

TF-IDF matrix is numerical representation of text where:

rows = documents
columns = words
values = TF-IDF scores
41. Why convert TF-IDF matrix into DataFrame?
pd.DataFrame()

makes matrix easier to view and analyze.

42. What does toarray() do?
tfidf_matrix.toarray()

Converts sparse matrix into normal array format.

43. What does get_feature_names_out() do?
tfidf.get_feature_names_out()

Returns words/features used in TF-IDF matrix.

44. What is unstructured data?

Unstructured data is data without predefined format.

Examples:

text
emails
social media posts
45. Why is preprocessing important in NLP?

Preprocessing:

removes noise
improves accuracy
simplifies text
reduces computation
46. What is the final conclusion of this practical?

This practical demonstrates text preprocessing techniques such as tokenization, POS tagging, stop word removal, stemming, and lemmatization, and creates document representation using TF-IDF for text analytics.
