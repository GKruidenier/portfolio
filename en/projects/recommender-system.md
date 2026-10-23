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
abstract: "On 27 million MovieLens ratings we compared two recommender techniques. After smart downsizing and tuning, the best one, based on taste profiles, is on average 0.8 stars off the real rating, versus 1.4 for guessing."
abstract_image: /assets/img/projects/recommender_abstract_en.svg
abstract_alt: "Visual summary: a mostly empty grid of viewers and films; SVD matches taste profiles and fills the empty cell with 4.2 stars, on average 0.8 stars off"
course: Analysis of Customer Data, May 2025
team: Three students (group 9)
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
  - name: "Similar films"
    tag: "KNN"
    text: "Looks at films the same people also liked or disliked. Easy to explain, but heavy on memory."
  - name: "Taste profiles"
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
  note: "One row per rating: 27 million rows from 283,228 viewers."
---

{% include slide.html kicker="Problem" title="What would you rate this film?" text="That is the core of every recommender system: filling in the empty cells, so you can recommend what someone will probably like." src="/assets/img/projects/recommender_probleem_en.svg" alt="Grid of viewers and films with filled-in ratings and empty cells; one empty cell is predicted as 4.2 stars" full=true %}

{% comment %} eerder: src="/assets/img/projects/recommender_cijfers_en.png" (eigen figuur) {% endcomment %}
{% include data.html kicker="Data" title="27 million ratings" text="Viewers mostly give high ratings: 4 stars is the most common, and half stars are given less often than whole stars." src="/assets/img/projects/recommender_nb_ratings.png" alt="Bar chart from the notebook: number of ratings per score from 0.5 to 5 stars. 4 stars is the most common (7.4 million), then 3 stars (5.5 million)." %}

{% include slide.html kicker="Data" title="A small group gives most ratings" text="Half of the viewers rated 30 films or fewer, but a few rated thousands; the most active viewer rated 23,715. Films show the same pattern. So the data is very uneven: most cells in the viewer-film grid are empty." src="/assets/img/projects/recommender_nb_per_gebruiker.png" alt="Histogram and boxplot from the notebook of the number of ratings per viewer. Almost all viewers sit close to zero, with a long tail up to 23,715 ratings." full=true %}


{% comment %} eerder: src="/assets/img/projects/recommender_pipeline_en.svg" (eigen figuur) {% endcomment %}
{% include slide.html kicker="Method" title="From 27 million to 3.1 million rows" text="We kept the most popular films and most active viewers and drew a stratified sample of 20%. The ratings in that sample are spread almost exactly like in the full dataset (left versus right, correlation 0.99). On this sample we trained, tuned and tested the models." src="/assets/img/projects/recommender_nb_vergelijking.png" alt="Two bar charts from the notebook: the share of each rating in the full dataset (left) and in the downsized dataset of 3.1 million rows (right). The two look almost the same (correlation 0.99)." full=true %}

{% include slide.html kicker="Method" title="Tuning the settings in two rounds" text="Each technique has settings you choose before training, such as how many similar films to look at. We searched for the best ones in two rounds (hyperparameter tuning). First a **random search**: 100 random combinations from a wide range. Then a **grid search**: every combination in a small range around the best one. Each combination was tested with 5-fold cross-validation, so always on ratings the model had not seen. The combination with the smallest error (RMSE) won." src="/assets/img/projects/recommender_nb_tuning.png" alt="Table: tuned settings, best combination and RMSE before and after tuning. KNNBaseline: k, min_k, similarity and shrinkage; best k = 38, min_k = 6, pearson_baseline, shrinkage 160; 0.830 to 0.814. SVD: n_factors, n_epochs, lr_all and reg_all; best 160, 55, 0.016 and 0.08; 0.838 to 0.803." full=true %}

{% comment %} eerder: zelfgemaakte grafiek recommender_resultaat_en.svg, daarna recommender_nb_rmse.png
{% include slide.html kicker="Results" title="On average 0.8 stars off" text="The error (RMSE) shows how many stars a prediction is off on average; lower is better. Guessing is 1.4 stars off. Both techniques are about 0.8 off, and tuning the settings (orange) made both a bit better. Taste profiles (SVD) end up closest, just ahead of similar films (KNN). With a different random split the result stayed practically the same." src="/assets/img/projects/recommender_nb_rmse.png" alt="Bar chart in the notebook style of the test RMSE per model with 5-fold cross-validation. Guessing (NormalPredictor) 1.425. KNNBaseline 0.830 with default settings and 0.814 tuned. SVD 0.838 with default settings and 0.803 tuned." full=true %}
{% endcomment %}
{% include slide.html kicker="Results" title="On average 0.8 stars off" text="The error (RMSE) shows how many stars a prediction is off on average; lower is better. Guessing is 1.4 stars off. Both techniques are about 0.8 off, and tuning made both a bit better. Taste profiles (SVD) end up closest, just ahead of similar films (KNN). **Why a second random split?** The tuned settings were chosen on one particular way of dividing the data into 5 parts (random seed 42). If a result only holds for that one division, it is luck rather than a good model. So we tested the tuned models again on a completely new random division (seed 101), and for SVD also with a new random start of the model itself. The error barely moved: KNN 0.8143 → 0.8142 and SVD 0.8032 → 0.8034. The tuned settings work on any split of the data, not just the one they were chosen on." src="/assets/img/projects/recommender_nb_resultaten.png" alt="Table of the test RMSE per model with 5-fold cross-validation. Guessing (NormalPredictor) 1.425. KNNBaseline 0.830 default, 0.814 tuned, 0.814 with another random split. SVD 0.838 default, 0.803 tuned, 0.803 with another random split." full=true %}

{% include slide.html kicker="Evaluation" title="Explainability or scale?" text="Similar films are easier to explain, but ran out of memory. Taste profiles are more accurate and scale better, but are less transparent." statement=true %}

<div class="role" markdown="1">
## My role
I did most of the work: data exploration, downsizing the data, tuning the models and validation.
</div>
