---
layout: project
lang: en
ref: citations
project: citations
section: master
title: Predicting how often a scientific paper will be cited
lead: "Can you predict how often a paper will be cited from its title, abstract, authors, venue and year?"
description: A natural language processing (NLP) pipeline with TF-IDF, Sentence-BERT and Ridge regression that predicts citation counts. Top 5 of the Machine Learning course.
abstract: "A natural language processing (NLP) pipeline that predicts how often a scientific paper will be cited from its title, abstract, authors, venue and year. A Ridge regression on term frequency–inverse document frequency (TF-IDF) and Sentence-BERT features finished in the top 5 of the course."
abstract_image: /assets/img/projects/citaties_abstract_en.svg
abstract_alt: "Visual summary: a paper is turned into numbers and a simple Ridge regression predicts its citation count; top 5 of the course"
course: Machine Learning, MSc Data Science and Society
team: Individual project
tools: [Python, scikit-learn, NLTK, TF-IDF, Sentence-BERT, Ridge, LightGBM, Random Forest]
stats:
  - value: "Top 5"
    label: "of all models in the course, on the leaderboard"
  - value: "> 2 GB"
    label: "of training data on scientific papers"
  - value: "1"
    label: "script runs the whole pipeline, from installation to prediction"
models:
  - name: "Linear models"
    tag: "linear regression, Lasso, Ridge"
    text: "Add up the features, each with a weight. Ridge regression penalises weights that grow too large (L2 regularisation)."
  - name: "Tree-based models"
    tag: "Random Forest, LightGBM"
    text: "Ensembles of many decision trees, including Light Gradient Boosting Machine (LightGBM). More powerful, but more sensitive to noise."
  - name: "Ridge regression"
    tag: "chosen model"
    own: true
    text: "Beat every other combination on the validation papers."
sample:
  caption: "What the data looks like"
  columns: ["Title", "Venue", "Year", "Citations"]
  rows:
    - ["Feature-based video mosaic", "ICIP", "2000", "51"]
    - ["Discovery of Frequent Word Sequences in Text", "LNCS", "2002", "15"]
    - ["A Fast Feature-based Dimension Reduction…", "Neural Processing Letters", "2006", "1"]
    - ["A Fully Integrated Humidity Sensor…", "Sensors", "2012", "8"]
  note: "Plus abstract, authors and references per paper; more than 2 GB in total."
---

{% include slide.html kicker="Problem" title="How much impact will this paper have?" text="Citations only add up after years. Can you estimate at publication how often a paper will be cited?" src="/assets/img/projects/citaties_probleem_en.svg" alt="Chart: after publication the number of citations builds up year by year; at the moment of publication it is still a question mark" full=true %}

{% include data.html kicker="Data" title="Text and details per paper" text="Citation counts are extremely skewed: most papers are cited rarely, a few very often." %}

{% include models.html kicker="Models" title="Simple versus complex" text="Dozens of combinations of features and models compared on papers the model had not seen." %}

{% include slide.html kicker="Method" title="From text to numbers" text="A model works with numbers, so I converted the text into features: TF-IDF scores for distinctive words, and Sentence-BERT embeddings for the meaning of the title. Sentence-BERT is a language model built on Bidirectional Encoder Representations from Transformers (BERT). The model predicts the square root of the citation count, so the few extremely cited papers do not dominate." src="/assets/img/projects/citaties_pipeline_en.svg" alt="Pipeline: title, abstract, authors, venue and year become TF-IDF features, Sentence-BERT embeddings and author and venue features, with which a Ridge regression predicts the citation count" full=true %}

{% include slide.html kicker="Results" title="Among the best five of the course" text="The teachers held back the real citation counts and ranked all predictions. My model finished among the five best of all students." src="/assets/img/projects/citaties_ranglijst_en.svg" alt="Illustration of the leaderboard: the top five places are highlighted, my model was in that group" big="Top 5" %}

{% include slide.html kicker="Evaluation" title="Simple wins" text="A Ridge regression on well-chosen features beat the heavier tree-based models. Extra features, such as an author's influence (h-index), added nothing." statement=true %}

<div class="role" markdown="1">
## My role
Individual project: I carried out every step myself, from text processing to the complete pipeline.
</div>
