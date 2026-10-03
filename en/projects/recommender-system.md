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
abstract: "On 27 million MovieLens ratings we compared a neighbourhood method (KNN) with matrix factorisation (SVD). After smart downsizing, tuning and double validation, the best SVD is on average less than one star off the real rating."
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
---

{% include slide.html title="Skewed data" text="One user gave 23,715 ratings, while half of the films have fewer than 7. Four stars is the most common rating." src="/assets/img/projects/recommender_verdeling_beoordelingen.png" alt="Bar chart of the rating distribution; 4 stars is most common" src2="/assets/img/projects/recommender_beoordelingen_per_gebruiker.png" alt2="Distribution of the number of ratings per user" full=true %}

{% include slide.html title="Smaller without losing anything" text="The full data did not fit in memory. A stratified sample of 3.1 million ratings kept 99% of the distribution." statement=true %}

{% include slide.html title="SVD wins" text="The tuned SVD reaches an RMSE of **0.803**. KNN follows at 0.814 and is easier to explain, but scales poorly." src="/assets/img/projects/recommender_rmse_vergelijking_en.png" alt="Bar chart of RMSE per model, before and after tuning" %}

<div class="role" markdown="1">
## My role
I did most of the work: data exploration, downsizing the dataset, tuning the models and validation.
</div>
