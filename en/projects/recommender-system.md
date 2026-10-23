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
{% include slide.html kicker="Method" title="From 27 million to 3.1 million rows" text="We kept the most popular films and most active viewers and drew a stratified sample of 20%. The ratings in that sample are spread almost exactly like in the full dataset (left versus right, correlation 0.99). Then we tuned the settings and tested on ratings the model had not seen." src="/assets/img/projects/recommender_nb_vergelijking.png" alt="Two bar charts from the notebook: the share of each rating in the full dataset (left) and in the downsized dataset of 3.1 million rows (right). The two look almost the same (correlation 0.99)." full=true %}

{% include slide.html kicker="Results" title="On average 0.8 stars off" text="Taste profiles (SVD) come closest to the real rating, just ahead of similar films (KNN). Guessing is 1.4 stars off. With a different random split the result stayed practically the same." src="/assets/img/projects/recommender_resultaat_en.svg" alt="Bar chart: guessing 1.43 stars off, similar films 0.81, taste profiles 0.80" full=true %}

{% include slide.html kicker="Evaluation" title="Explainability or scale?" text="Similar films are easier to explain, but ran out of memory. Taste profiles are more accurate and scale better, but are less transparent." statement=true %}

<div class="role" markdown="1">
## My role
I did most of the work: data exploration, downsizing the data, tuning the models and validation.
</div>
