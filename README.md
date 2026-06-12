# IMDB Sentiment Analysis

## Problem

text is hard because it is not as numbers that the models can process. And that the models cant distinguish between the context and meaning and the word sequence
## Dataset

source: IMDB movie reviews, size: (2000, 2) , equal balance of positive and negative reviews
## Approach

I started with lowercasing all of the sentences, removing all of the special characters and punctuations, splitted the sentences into words and removed stop words that repeat in the english language, and stripped down the words to their base form. I used BOW (bag of words) and TF-IDF they both convert words into numbers but the approach they use is different  BOW counts how many times a word appears without considering its importance while TF-IDF counts how many times it appears while also counting how rare it is as how many times it appears. I compared 6  models : 
 NaiveBayes_TF-IDF,
 NaiveBayes_BOW,
 LogReg_TF-IDF,
 XGBoost_BOW,
 XGBoost_TFIDF,
 LogReg_BOW
## Results

| Model | Accuracy |
|-------|----------|
|LogReg_BOW|0.85|
|XGBoost_TFIDF|0.8475|
|XGBoost_BOW|0.835|
|LogReg_TF-IDF|0.83|
|NaiveBayes_BOW|0.81|
|NaiveBayes_TF-IDF| 0.8|
## Key Finding

best model: LogReg+BOW, the BOW vs TF-IDF surprise: BOW won even when TF-IDF is 'smarter' but BOW won because when a word like excellent or some positive or negative words is used more it is presumed that the sentence and review is more leaned towards what type of words is , error analysis insight about context/word order : that even if it has some positive or negative words but the whole sentence and review is negative the models still lean to positive or negative based on some words that are there

## What Would Improve This Model

1. Word embeddings (Word2Vec/GloVe) these represent words as vectors where similar-meaning words are close together (e.g., "great" and "excellent" end up near each other mathematically). This helps each word to be better added up 

2. BERT / Transformers  these read the whole sentence at once and understand context, including sarcasm and negation. It understands that words that are negative describe the movies subjects matter rather than reviewers opinion, which BOW cant distinguish

3. N-grams (pairs of words instead of single words) that when there is like a word good and not good the model would think that both are positive but when there is the not it is negative so this fixes that it will pair the words and the model will be able to better to distinguish the pairs and sentiment of the words 