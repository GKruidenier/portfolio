---
layout: project
lang: en
ref: citations
project: citations
section: master
title: Predicting how often a scientific paper will be cited
lead: "Can you predict how often a paper will be cited from its title, abstract, authors, venue and year?"
description: An NLP and regression pipeline (TF-IDF, Sentence-BERT, Ridge) that predicts citation counts. Top 5 of the Machine Learning course.
abstract: "A reproducible pipeline that predicts how often a paper will be cited from its title, abstract, authors, venue and year. A simple Ridge regression on well-chosen features finished in the top 5 of the course."
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
  - name: "Linear models"
    tag: "compared"
    text: "Linear regression, Lasso and Ridge: features with a weight."
  - name: "Tree models"
    tag: "compared"
    text: "Random Forest and LightGBM: many decision trees together."
  - name: "Ridge"
    tag: "chosen"
    own: true
    text: "Linear, with a brake on overly large weights."
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

{% include slide.html kicker="Problem" title="How much impact will this paper have?" text="Citations only add up after years. Can you predict the count at publication?" src="/assets/img/projects/citaties_probleem_en.svg" alt="Sketch: a paper with title, authors, venue and abstract goes into a model that predicts its citation count" full=true %}

{% include data.html kicker="Data" title="Text and metadata per paper" text="Citation counts are extremely skewed: most papers are cited rarely, a few very often." %}

{% include models.html kicker="Models" title="Simple versus complex" text="Dozens of combinations of features and models compared on a separate validation set." %}

{% include slide.html kicker="Method" title="From text to numbers" text="TF-IDF finds distinctive words, Sentence-BERT captures the meaning of the title. The model predicts the square root of the citation count." src="/assets/img/projects/citaties_pipeline_en.svg" alt="Pipeline: title, abstract, authors, venue and year become features via TF-IDF, Sentence-BERT and metadata for a Ridge regression" full=true %}

{% include slide.html kicker="Results" title="Among the best five of the course" text="On the teachers' leaderboard, who held the true citations, my model finished among the five best of all students." big="Top 5" %}

{% include slide.html kicker="Evaluation" title="Simple wins" text="A linear model beat the heavier tree models. Extra features such as authors' h-index added nothing." statement=true %}

<div class="role" markdown="1">
## My role
Individual project: I carried out every step myself, from text processing to the pipeline.
</div>
