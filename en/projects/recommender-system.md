---
layout: project
lang: en
ref: recommender
project: recommender
section: master
title: Film recommendations from 27 million ratings
lead: How well can you predict the rating someone will give a film they haven't seen yet? That is the core of every recommender system, from Netflix to an online shop.
description: A recommender system on the MovieLens data with KNNBaseline and SVD, tuned and validated. RMSE 0.803.
image: /assets/img/projects/recommender_rmse_vergelijking_en.png
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

## The question

How well can you predict the rating a user will give to a film they haven't seen yet? That is the core of every recommender system, from Netflix to an online shop.

## The data

The MovieLens dataset: over 27 million ratings (0.5 to 5 stars) from 283,228 users for 53,889 films. The data is extremely skewed: a small group of very active users gives most of the ratings (one user rated 23,715 films), while half of the films have fewer than 7 ratings.

<div class="figure-pair">
{% include figure.html src="/assets/img/projects/recommender_verdeling_beoordelingen.png" alt="Bar chart of the rating distribution; 4 stars is the most common" caption="How users rate films: 4 stars is the most common rating." %}
{% include figure.html src="/assets/img/projects/recommender_beoordelingen_per_gebruiker.png" alt="Distribution of the number of ratings per user" caption="The skewed activity per user." %}
</div>

## Approach

- **Shrinking the data without losing information.** On the full dataset the models ran out of memory. I selected the 4,000 most-rated films and 40,000 most active users and drew a stratified sample of 3.1 million ratings from them. The rating distribution stayed 99% identical to the original.
- **Comparing three models.** A random predictor as a lower bound (NormalPredictor), a neighbourhood method based on similar films (KNNBaseline) and matrix factorisation (SVD).
- **Tuning and checking.** Hyperparameters were searched with a randomized search followed by a grid search, using 5-fold cross-validation, and then validated again with a different random seed to check the results are stable.

## Results

{% include figure.html src="/assets/img/projects/recommender_rmse_vergelijking_en.png" alt="Bar chart of RMSE per model, before and after tuning" caption="The models compared before and after tuning. Lower is better." %}

- **The tuned SVD is the most accurate, with an RMSE of 0.803.** On average its prediction is less than one star away from the real rating. The random baseline was 1.43 stars off.
- KNNBaseline comes close (0.814) and is easier to explain, but scales badly: the user-based version ran out of memory, so we switched to comparing films instead.
- With a different seed the RMSE changed by only 0.0002, so the chosen settings are robust.

> **Recommendation:** choose KNN when explainability matters and the dataset is limited, and SVD when accuracy and scale matter more.

<div class="role" markdown="1">
## My role
I carried out most of this project: data exploration, reducing the dataset, configuring and tuning the models, and validating and evaluating the results.
</div>
