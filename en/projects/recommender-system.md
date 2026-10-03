---
layout: project
lang: en
ref: recommender
project: recommender
section: master
title: Film recommendations from 27 million ratings
lead: "How well can you predict the rating someone will give a film they haven't seen yet?"
description: A recommender system on the MovieLens data with KNNBaseline and SVD, tuned and validated. RMSE 0.803.
image: /assets/img/projects/recommender_rmse_vergelijking_en.png
abstract: "On 27 million MovieLens ratings we compared two recommender techniques. After smart downsizing and tuning, the best one (SVD) is on average 0.8 stars off the real rating, versus 1.4 for guessing."
abstract_image: /assets/img/projects/recommender_abstract_en.svg
abstract_alt: "Visual summary: a mostly empty grid of viewers and films; SVD matches taste profiles and fills the empty cell with 4.2 stars, on average 0.8 stars off"
course: Analysis of Customer Data, May 2025
team: Three students (group 9)
tools: [Python, pandas, Surprise, Collaborative filtering, KNN, SVD, Hyperparameter tuning]
stats:
  - value: "0.803"
    label: RMSE of the tuned SVD
  - value: "27M"
    label: ratings in the full dataset
  - value: "99%"
    label: same distribution after smart downsizing
models:
  - name: "NormalPredictor"
    tag: "baseline"
    text: "Guesses a rating from the overall distribution."
  - name: "KNNBaseline"
    tag: "model"
    text: "Looks at films the same people rated similarly."
  - name: "SVD"
    tag: "model"
    own: true
    text: "Summarises viewers and films as hidden taste factors."
sample:
  caption: "What the data looks like"
  columns: ["Viewer", "Film", "Rating", "Date"]
  rows:
    - ["1", "307", "3.5", "27 Oct 2009"]
    - ["1", "481", "3.5", "27 Oct 2009"]
    - ["1", "1091", "1.5", "27 Oct 2009"]
    - ["1", "1257", "4.5", "27 Oct 2009"]
  note: "One row per rating: 27 million rows from 283,228 viewers."
---

{% include slide.html kicker="Problem" title="What would you rate this film?" text="That is the core of every recommender system: filling in the empty cells, so you can recommend what someone will probably like." src="/assets/img/projects/recommender_probleem_en.svg" alt="Grid of viewers and films with filled-in ratings and empty cells; one empty cell is predicted as 4.2 stars" full=true %}

{% include data.html kicker="Data" title="27 million ratings" text="Viewers mostly give high ratings, and a small group gives most of them." src="/assets/img/projects/recommender_cijfers_en.png" alt="Bar chart of the rating distribution; 4 stars is the most common" %}

{% include models.html kicker="Models" title="Three ways to predict a rating" %}

{% include slide.html kicker="Method" title="From 27 million to 3.1 million rows" text="We kept the most popular films and most active viewers and took a sample with 99% the same distribution. Then tuning with 5-fold cross-validation." src="/assets/img/projects/recommender_pipeline_en.svg" alt="Pipeline: viewer, film and rating are downsized and sampled, then SVD predicts the rating for an unseen film" full=true %}

{% include slide.html kicker="Results" title="SVD wins: 0.80 stars off" text="Guessing is 1.43 stars off, KNN 0.81. With another seed the error changed by only 0.0002." src="/assets/img/projects/recommender_rmse_vergelijking_en.png" alt="Bar chart of the error (RMSE) per model, before and after tuning" %}

{% include slide.html kicker="Evaluation" title="Explainability or scale?" text="KNN is easier to explain, but ran out of memory. SVD is more accurate and scales better, but is less transparent." statement=true %}

<div class="role" markdown="1">
## My role
I did most of the work: data exploration, downsizing the data, tuning and validation.
</div>
