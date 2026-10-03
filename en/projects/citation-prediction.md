---
layout: project
lang: en
ref: citations
project: citations
section: master
title: Predicting how often a scientific paper will be cited
lead: Can you predict how often a paper will be cited from its title, abstract, authors, venue and year?
description: An NLP and regression pipeline (TF-IDF, Sentence-BERT, Ridge) that predicts citation counts. Top 5 of the Machine Learning course.
course: Machine Learning, MSc Data Science and Society
team: Individual project
tools: [Python, scikit-learn, NLTK, TF-IDF, Sentence-BERT, Ridge, LightGBM, Random Forest]
stats:
  - value: "Top 5"
    label: of all models in the course, on the leaderboard
  - value: "> 2 GB"
    label: of training data on scientific papers
  - value: "1"
    label: script runs the whole pipeline, from installation to prediction
---

## The question

Can you predict how often a scientific paper will be cited from its title, abstract, authors, venue and year?

## The data

A large dataset of scientific papers (the training data alone is over 2 GB), with each paper's title, abstract, authors, venue, publication year, references and citation count. Citation counts are extremely skewed: most papers are cited rarely, a few very often.

## The pipeline

<ol class="pipeline">
  <li><strong>Clean text</strong>Remove stop words, lemmatise with NLTK</li>
  <li><strong>Text features</strong>TF-IDF on abstract and title, Sentence-BERT embeddings of the title</li>
  <li><strong>Metadata</strong>Authors, venue, decade and average citations of references</li>
  <li><strong>Target</strong>Square root of the citation count, to handle the skew</li>
  <li><strong>Ridge regression</strong>Best model after dozens of compared combinations</li>
</ol>

## Approach

- **Turning text into features.** Abstracts and titles were cleaned (stop words removed, lemmatised) and converted with TF-IDF. Titles were also converted into meaning vectors with the Sentence-BERT language model (all-MiniLM-L6-v2).
- **Author and venue features.** Authors encoded as full names with TF-IDF, plus venue, decade and the average citation count of the papers a paper references. H-index, first-author experience and citations per venue were also tested.
- **Transforming the target.** Because of the skew the model predicts the square root of the citation count; linear, logarithmic and square-root targets were compared.
- **Systematic comparison.** Dozens of feature and model combinations (linear regression, Lasso, Ridge, Random Forest, LightGBM, XGBoost) tested on a separate validation set, with mean absolute error (MAE) as the metric.
- **Reproducible pipeline.** The whole chain of installation, embeddings, training and predictions runs from one script.

## Results

- The best model was a Ridge regression on the combination of abstract, title, authors, venue, decade, average reference citations and title embeddings.
- Predictions were submitted to a leaderboard, with the lecturers holding the true citation counts of the test set. **My model finished among the five best models in the course.**
- Notably, a simple linear model on well-chosen features beat the heavier tree models such as LightGBM and Random Forest.

<div class="role" markdown="1">
## My role
Individual project: I did every step myself, from feature engineering and text processing to model selection and the reproducible pipeline.
</div>
