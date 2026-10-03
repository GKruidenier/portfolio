---
layout: project
lang: en
ref: citations
project: citations
section: master
title: Predicting how often a scientific paper will be cited
lead: "Can you predict how often a paper will be cited from its title, abstract, authors, venue and year?"
description: An NLP and regression pipeline (TF-IDF, Sentence-BERT, Ridge) that predicts citation counts. Top 5 of the Machine Learning course.
abstract: "A reproducible NLP and regression pipeline on more than 2 GB of scientific papers. Text is converted with TF-IDF and Sentence-BERT, combined with metadata, and a Ridge regression predicts the number of citations. The model finished in the top 5 of the course."
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
models:
  - name: "Linear regression, Lasso and Ridge"
    tag: "linear"
    text: "Add up the features with a weight. Ridge and Lasso penalise large weights, which helps with thousands of text features."
  - name: "Random Forest and LightGBM"
    tag: "trees"
    text: "Combine many decision trees and can learn complex patterns, but are heavier and more sensitive to noise."
  - name: "Ridge on the best features"
    tag: "chosen"
    own: true
    text: "Beat every other combination: a simple model on well-chosen features."
---

{% include slide.html kicker="Problem" title="Which paper will have impact?" text="Citations measure scientific impact, but they only add up after years. Can you estimate at publication how often a paper will be cited, using only its title, abstract, authors, venue and year?" %}

{% include slide.html kicker="Data" title="More than 2 GB of papers" text="For each paper: title, abstract, authors, venue, year, references and the citation count. That count is extremely skewed: most papers are cited rarely, a few very often. So the model predicts its square root." %}

{% include slide.html kicker="Data" title="From text to numbers" text="A model works with numbers, so text has to be converted first. TF-IDF counts which words are distinctive, Sentence-BERT captures the meaning of the title in a vector." src="/assets/img/projects/citaties_pipeline_en.svg" alt="Diagram: title, abstract, authors, venue and year are turned into features via TF-IDF, Sentence-BERT and metadata for a Ridge regression" full=true %}

{% include models.html kicker="Models" title="Simple versus complex" text="Dozens of combinations of features and models compared on a separate validation set." %}

{% include slide.html kicker="Method" title="One reproducible pipeline" text="The whole chain, from installation and embeddings to training and predictions, runs with one script." src="/assets/img/projects/citaties_methode_en.svg" alt="Six-step method diagram: data, text cleaning, features, target, models and evaluation" full=true %}

{% include slide.html kicker="Results" title="Top 5 of the course" text="Predictions were submitted to a leaderboard where the teachers held the true citations. My model finished among the five best of all students." statement=true %}

{% include slide.html kicker="Evaluation" title="What worked, and what didn't" text="Abstract, title, authors, venue, decade and the citations of references contributed most. Extra features such as h-index and first-author experience, and heavier tree models, did not improve the result." %}

<div class="role" markdown="1">
## My role
Individual project: from text processing and feature engineering to model selection and the pipeline.
</div>
