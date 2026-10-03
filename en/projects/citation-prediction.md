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
---

{% include slide.html title="The pipeline" text="Text and metadata become features. A Ridge regression predicts the square root of the citation count, to handle the skewed distribution. One script runs it all." src="/assets/img/projects/citaties_pipeline_en.svg" alt="Diagram: title, abstract, authors, venue and year are turned into features via TF-IDF, Sentence-BERT and metadata for a Ridge regression" full=true %}

{% include slide.html title="Simple wins" text="After comparing dozens of combinations, a linear model on well-chosen features beat LightGBM and Random Forest. Top 5 of all models in the course." statement=true %}

<div class="role" markdown="1">
## My role
Individual project: from text processing and feature engineering to model selection and the pipeline.
</div>
