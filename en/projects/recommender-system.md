---
layout: project
lang: en
ref: recommender
project: recommender
section: master
title: Building a film recommendation system from movie ratings
lead: "How well can you predict the rating someone will give a film they haven't seen yet?"
description: A recommender system on the MovieLens data with KNNBaseline and SVD, tuned and validated. RMSE 0.803.
image: /assets/img/projects/recommender_rmse_vergelijking_en.png
abstract: |
  ### The problem

  We had to build two recommender systems on the MovieLens data (27.7 million film ratings from 283,228 viewers, 1995 to 2018) and compare them to eachother and with guessing. One had to be a neighbourhood method, and the other matrix factorisation.

  ### Our solution

  The methods we chose were k-nearest neighbours (KNN), and singular value decomposition (SVD). Each was tuned and tested with 5-fold cross-validation.

  We first kept the most active viewers and most-rated films (top-k filtering) and then used stratified sampling to create a representative sample, downsizing the original data to 3.1 million ratings with the same distribution of ratings (correlation 0.99 with the original rating distribution). This cut training time dramatically and made it feasible to tune both techniques in two search rounds.

  ### Result

  The best method, SVD, is on average 0.8 stars off the real rating. Guessing is 1.4 stars off. On a second random split of the data the result stayed the same.
abstract_image: /assets/img/projects/recommender_mpl_abstract.png
abstract_alt: "Three panels. Left: a mostly empty grid of viewers and films (27.7 million ratings, downsized to a 3.1 million sample) with one empty cell to predict. Middle: two ways to fill the cell, KNN (looks at films the same viewers rated alike) and SVD (learns hidden preferences of viewers and films). Right: bar chart of the error (RMSE, lower is better) with 5-fold cross-validation: guessing 1.425, KNN tuned 0.814, SVD tuned 0.803."
course: Analysis of Customer Data, May 2025
team: "Three students (group 9). My role: I did most of the work (data exploration, downsizing the data, tuning the models and validation)."
tools: [Python, pandas, Surprise, Collaborative filtering, KNN, SVD, Hyperparameter tuning]
stats:
  - value: "0.8 ★"
    label: "off on average for a predicted rating (guessing: 1.4)"
  - value: "27M"
    label: "ratings in the full dataset"
  - value: "99%"
    label: "same distribution after smart downsizing"
models:
  - name: "Guessing"
    tag: "NormalPredictor"
    text: "Picks a random rating from the overall distribution."
  - name: "k-nearest neighbours"
    tag: "KNN"
    text: "Looks at films the same people also liked or disliked. Easy to explain, but heavy on memory."
  - name: "Singular value decomposition"
    tag: "SVD"
    own: true
    text: "Summarises viewers and films in a few hidden taste traits and checks how well they match."
sample:
  caption: "What the data looks like"
  columns: ["Viewer", "Film", "Rating", "Date"]
  rows:
    - ["1", "307", "3.5", "27 Oct 2009"]
    - ["1", "481", "3.5", "27 Oct 2009"]
    - ["1", "1091", "1.5", "27 Oct 2009"]
    - ["1", "1257", "4.5", "27 Oct 2009"]
  note: "One row per rating: 27.7 million rows from 283,228 viewers."
---

{% include slide.html kicker="Problem" title="What would you rate this film?" text="The core of every recommender system is: predicting the rating of items that the user hasn't seen yet, so you can recommend the ones someone will probably like.  In this assignment, these items were movies from the MovieLens dataset (27.7 million ratings of 58,098 films by 283,228 viewers, half stars from 0.5 to 5).

We built two recommender systems with the Python library Surprise: a KNN model, which looks at films that the same viewers rated alike, and an SVD model, which learns hidden preferences of viewers and films. We tuned both and compare them with a model that guesses randomly (using a normal distribution derived from the data). We used 5-fold cross-validation and the root mean squared error (RMSE): roughly how many stars a prediction is off on average." src="/assets/img/projects/recommender_probleem_en.svg" alt="Grid of viewers and films with filled-in ratings and empty cells; one empty cell is predicted as 4.2 stars" full=true %}

{% comment %} eerdere slides 2, 3 en 4 (Data: 27 million ratings / A small group gives most ratings / From 27 million to 3.1 million rows):
{% comment %} eerder: src="/assets/img/projects/recommender_cijfers_en.png" (eigen figuur) {% endcomment %}
{% include data.html kicker="Data" title="27 million ratings" text="Viewers mostly give high ratings: 4 stars is the most common, and half stars are given less often than whole stars." src="/assets/img/projects/recommender_nb_ratings.png" alt="Bar chart from the notebook: number of ratings per score from 0.5 to 5 stars. 4 stars is the most common (7.4 million), then 3 stars (5.5 million)." %}

{% include slide.html kicker="Data" title="A small group gives most ratings" text="Half of the viewers rated 30 films or fewer, but a few rated thousands; the most active viewer rated 23,715. Films show the same pattern. So the data is very uneven: most cells in the viewer-film grid are empty." src="/assets/img/projects/recommender_nb_per_gebruiker.png" alt="Histogram and boxplot from the notebook of the number of ratings per viewer. Almost all viewers sit close to zero, with a long tail up to 23,715 ratings." full=true %}


{% comment %} eerder: src="/assets/img/projects/recommender_pipeline_en.svg" (eigen figuur) {% endcomment %}
{% include slide.html kicker="Method" title="From 27 million to 3.1 million rows" text="**Why a sample?** The full dataset was too large to work with. KNN builds a similarity matrix between all films, which ran out of memory, and hyperparameter tuning means fitting every model hundreds of times (the random search alone is 100 combinations × 5 folds = 500 fits). Even on the final sample, the random search for SVD took 50 minutes. So we reduced the data in two steps, and trained, tuned and tested all models on the result." points="**1. Top-k filtering:** a small group of films and viewers gives most of the ratings (a long-tail distribution). We kept the 4,000 most-rated films and the 40,000 most active viewers, which also carry the most reliable preference information: 15.5 million rows, still too many. | **2. Stratified sampling:** from those rows we drew 20%, stratified on the rating. A plain random sample can by chance take too many or too few of the rare ratings (0.5 and 1.5 stars are each only 1.6% of the data). Stratified sampling draws 20% from every rating level separately, so the sample keeps exactly the same distribution of ratings: 3.1 million rows. | **Check:** the ratings in the final sample are spread almost the same as in the full dataset (left versus right, correlation 0.99)." src="/assets/img/projects/recommender_nb_vergelijking.png" alt="Two bar charts from the notebook: the share of each rating in the full dataset (left) and in the downsized dataset of 3.1 million rows (right). The two look almost the same (correlation 0.99)." full=true %}
{% endcomment %}

{% comment %} eerdere slide 2 (sparsity), samengevoegd met top-k:
{% include slide.html kicker="Data" title="27.7 million ratings, yet 99.8% empty" text="The MovieLens data is huge and at the same time **sparse**: of the 15.3 billion possible viewer-film combinations, only 0.18% has a rating. The ratings are also very unevenly spread. **Few films get many ratings:** the 7% most-rated films get 90% of all ratings, while half of all films have 7 ratings or fewer. **Few viewers give many ratings:** the 14% most active viewers give 65% of all ratings, while half of all viewers rated 30 films or fewer. This gives a problem: for many films and viewers there are so few ratings that there is not enough information for the model to make accurate predictions. The solution, **top-k filtering**, is explained on the next slide." src="/assets/img/projects/recommender_mpl_sparsity.png" alt="Left: a random piece of 300 viewers by 300 films from the real rating matrix; only 136 of the 90,000 cells have a rating. Right: table with key numbers: 27,753,444 ratings, 283,228 viewers, 53,889 films with at least one rating, 15.3 billion possible combinations, 0.18% rated, median 30 ratings per viewer, median 7 ratings per film, 58% of films have 10 ratings or fewer." full=true %}
{% endcomment %}

{% include slide.html kicker="Data" title="Step 1: sparse data and top-k filtering" text="The MovieLens data is huge and sparse: of the 15.3 billion possible viewer-film combinations, only 0.18% has a rating. The ratings follow a long-tail distribution (see the curves). The 7% most-rated films get 90% of all ratings, while half of all films have 7 or fewer. And the 14% most active viewers give 65% of the ratings, while half of all viewers rated 30 films or fewer. This poses a problem: for films and viewers with few ratings there is too little information to make accurate predictions.

To solve this, we applied top-k filtering: we kept only the 4,000 most-rated films (at least 969 ratings each), the 40,000 most active viewers (at least 175 each). This cut the data from 27.7 million to 15.5 million ratings, and the grid went from 0.18% to 10% filled. This also kept KNN workable: its similarity matrix between all pairs of films shrank from about 2.9 billion to 16 million values." src="/assets/img/projects/recommender_nb_topk.png" alt="Line chart from the notebook: relative frequency of the ratings for the top 15,000 films, sorted from most to least rated. The curve drops steeply after the first few hundred films; a dashed line marks the top 4,000 films that were kept." src2="/assets/img/projects/recommender_nb_topk_users.png" alt2="Line chart from the notebook: relative frequency of the ratings for the top 50,000 viewers, sorted from most to least active. A few viewers give very many ratings, then the curve flattens; a dashed line marks the top 40,000 viewers that were kept." full=true %}

{% comment %} eerder: src="/assets/img/projects/recommender_nb_vergelijking.png" (twee losse grafieken) {% endcomment %}
{% include slide.html kicker="Method" title="Step 2: stratified sampling, from 15.5 to 3.1 million rows" text="Top-k filtering reduced the data to 15.5 million ratings, but that was still too big to train and tune on: hyperparameter tuning means fitting every model hundreds of times (the random search alone is 100 combinations × 5 folds = 500 fits). Even on the final sample, the random search for SVD took 50 minutes.

The solution was to apply stratified sampling. Stratified sampling differs from plain random sampling because the latter can by chance take too many or too few of the rare ratings (0.5 and 1.5 stars are each only 1.6% of the data). Stratified sampling draws 20% from every rating level separately, so the sample keeps exactly the same distribution of ratings: 3.1 million rows.

All models were trained, tuned and tested on this final sample. As visualised below, the ratings in this sample are spread almost the same as in the original full dataset (blue bars versus red outlines, correlation 0.99)." src="/assets/img/projects/recommender_nb_vergelijking_overlay.png" alt="Bar chart with the share of each rating, from 0.5 to 5 stars, in the original dataset and the reduced dataset of 3.1 million rows laid over each other: the original as light blue bars, the sample as red outlines. The bars are almost the same height (correlation 0.99); the largest difference is at 5 stars, 14.7% versus 12.0%." full=true %}

{% include slide.html kicker="Method" title="Tuning the settings in two rounds" text="Each technique has settings you choose before training, such as how many similar films to look at. We searched for the best ones in two rounds (hyperparameter tuning). First a random search: 100 random combinations from a wide range. Then a grid search: every combination in a small range around the best one. Each combination was tested with 5-fold cross-validation, so always on ratings the model had not seen. The combination with the smallest error (RMSE) won." src="/assets/img/projects/recommender_nb_tuning.png" alt="Table: tuned settings, best combination and RMSE before and after tuning. KNNBaseline: k, min_k, similarity and shrinkage; best k = 38, min_k = 6, pearson_baseline, shrinkage 160; 0.830 to 0.814. SVD: n_factors, n_epochs, lr_all and reg_all; best 160, 55, 0.016 and 0.08; 0.838 to 0.803." full=true %}

{% comment %} eerder: zelfgemaakte grafiek recommender_resultaat_en.svg, daarna recommender_nb_rmse.png
{% include slide.html kicker="Results" title="On average 0.8 stars off" text="The error (RMSE) shows how many stars a prediction is off on average; lower is better. Guessing is 1.4 stars off. Both techniques are about 0.8 off, and tuning the settings (orange) made both a bit better. Taste profiles (SVD) end up closest, just ahead of similar films (KNN). With a different random split the result stayed practically the same." src="/assets/img/projects/recommender_nb_rmse.png" alt="Bar chart in the notebook style of the test RMSE per model with 5-fold cross-validation. Guessing (NormalPredictor) 1.425. KNNBaseline 0.830 with default settings and 0.814 tuned. SVD 0.838 with default settings and 0.803 tuned." full=true %}
{% endcomment %}
{% comment %} eerder: src="/assets/img/projects/recommender_nb_resultaten.png" (tabel) {% endcomment %}
{% include slide.html kicker="Results" title="On average 0.8 stars off" text="The error (RMSE) shows how many stars a prediction is off on average; lower is better. Guessing is 1.4 stars off. Both techniques are about 0.8 off, and tuning made both a bit better. SVD ends up closest, just ahead of KNN.

**Why a second random split?** The tuned settings were chosen on one particular way of dividing the data into 5 parts (random seed 42). If a result only holds for that one division, it is luck rather than a good model. So we tested the tuned models again on a completely new random division (seed 101), and for SVD also with a new random start of the model itself. The error barely moved: KNN 0.8143 → 0.8142 and SVD 0.8032 → 0.8034. The tuned settings work on any split of the data, not just the one they were chosen on." src="/assets/img/projects/recommender_mpl_resultaten.png" alt="Two charts. Left: bar chart of the error (RMSE) with 5-fold cross-validation: guessing (NormalPredictor) 1.425, KNN tuned 0.814, SVD tuned 0.803; both models have about 44% lower error than guessing. Right: zoom on KNN and SVD: tuning moves KNN from 0.8300 to 0.8143 and SVD from 0.8378 to 0.8032; on another random split the tuned models score 0.8142 and 0.8034." full=true %}

{% include slide.html kicker="Discussion" title="Explainability or scale?" text="Both models beat guessing by far, and after tuning they are close: SVD is only 0.011 stars more accurate than KNN. The bigger difference is in how they work. KNN is easy to explain (‘viewers who liked this film also liked that one’), but it has to store the similarity between every pair, which only fit in memory once we compared films instead of viewers. SVD learns compact hidden preferences, so it scales better to large data, but those preferences cannot be explained. KNN suits smaller datasets where explainability matters; SVD suits large systems where accuracy and scale matter." %}
