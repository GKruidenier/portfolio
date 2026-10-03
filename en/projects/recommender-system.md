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
models:
  - name: "NormalPredictor"
    tag: "baseline"
    text: "Guesses a rating from the overall distribution, ignoring user and film."
  - name: "KNNBaseline"
    tag: "model"
    text: "Finds films rated similarly by the same people. Easy to explain, but heavy on memory."
  - name: "SVD"
    tag: "model"
    text: "Summarises users and films as hidden 'taste factors' and predicts the rating from how well they match."
---

{% include slide.html kicker="Problem" title="Which film will someone like?" text="A streaming service wants to recommend films people will really enjoy. That comes down to one question: what rating would this user give a film they have not seen yet?" %}

{% include slide.html kicker="Data" title="27 million ratings, very skewed" text="283,228 users and 53,889 films. Four stars is the most common rating. One user gave 23,715 ratings, while half of the films have fewer than 7." src="/assets/img/projects/recommender_verdeling_beoordelingen.png" alt="Bar chart of the rating distribution; 4 stars is most common" src2="/assets/img/projects/recommender_beoordelingen_per_gebruiker.png" alt2="Distribution of the number of ratings per user" full=true %}

{% include slide.html kicker="Data" title="A small top gets almost all attention" text="A small share of films attracts most of the ratings. So we worked with the 4,000 most popular films and 40,000 most active users, and a sample of 3.1 million ratings with 99% the same distribution." src="/assets/img/projects/recommender_long_tail.png" alt="Line chart: the relative frequency of ratings drops steeply across the most popular films" %}

{% include models.html kicker="Models" title="Three ways to predict a rating" text="Two well-known recommender techniques (collaborative filtering), compared with a random predictor." %}

{% include slide.html kicker="Method" title="From 27 million rows to a tuned model" text="First explore and downsize, then tune with cross-validation and re-test the best settings with another seed." src="/assets/img/projects/recommender_methode_en.svg" alt="Six-step method diagram: data, exploration, downsizing, models, tuning and evaluation" full=true %}

{% include slide.html kicker="Results" title="SVD wins" text="The tuned SVD is on average **0.80 stars** off the real rating, versus 1.43 for guessing. KNN follows at 0.81. With another seed the error changed by only 0.0002." src="/assets/img/projects/recommender_rmse_vergelijking_en.png" alt="Bar chart of RMSE per model, before and after tuning" %}

{% include slide.html kicker="Evaluation" title="Explainability or scale?" text="KNN is easier to explain, but ran out of memory when comparing users. SVD is more accurate and scales better, but its taste factors cannot be interpreted. Our advice: KNN when explanation matters, SVD when scale matters." statement=true %}

<div class="role" markdown="1">
## My role
I did most of the work: data exploration, downsizing the dataset, tuning the models and validation.
</div>
