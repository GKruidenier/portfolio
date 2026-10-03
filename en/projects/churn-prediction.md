---
layout: project
lang: en
ref: churn
project: churn
section: master
title: Which players will quit? Predicting churn in a mobile game
lead: "Can you tell after the first few days whether a new player will stay or quit?"
description: Churn defined from raw play logs and predicted with logistic regression, Random Forest and XGBoost. Highest grade of all groups.
image: /assets/img/projects/churn_modelvergelijking_prauc_en.png
abstract: "From 150,000 games of a mobile game we defined ourselves when a player has quit. Using eight behavioural features, our models predict after five days who will return, almost five times better than guessing. Highest grade of all groups."
course: Analysis of Customer Data, autumn 2025
team: Four students (group 5) · highest grade of all groups
tools: [Python, pandas, scikit-learn, XGBoost, Feature engineering, Cross-validation]
stats:
  - value: "5×"
    label: better than guessing (PR-AUC 0.38 vs 0.08)
  - value: "2 in 3"
    label: predicted returners actually return
  - value: "0.79"
    label: ROC-AUC of the best model
models:
  - name: "Guessing"
    tag: "lower bound"
    text: "Without a model you catch 7.9% of returners."
  - name: "Logistic regression"
    tag: "model"
    text: "Adds up the features with a fixed weight."
  - name: "Random Forest"
    tag: "model"
    text: "Hundreds of decision trees that vote together."
  - name: "XGBoost"
    tag: "model"
    own: true
    text: "Trees that correct each other's mistakes step by step."
sample:
  caption: "What the data looks like"
  columns: ["Player", "Timestamp", "Score"]
  rows:
    - ["3526…9119", "13 Jan 2015 13:54", "0"]
    - ["3526…9119", "13 Jan 2015 13:55", "7"]
    - ["3526…9119", "13 Jan 2015 13:55", "6"]
    - ["3526…9119", "14 Jan 2015 00:38", "252"]
  note: "One row per game played: 153,929 rows, nothing else."
---

{% include slide.html kicker="Problem" title="When has a player quit?" text="There is no subscription to cancel. We follow a new player for five days and predict whether they come back afterwards." src="/assets/img/projects/churn_probleem_en.svg" alt="Timeline: three players are followed for five days; only player C plays again in the twelve days after and counts as a stayer" full=true %}

{% include data.html kicker="Data" title="Only a timestamp, a score and an ID" text="Most new players are gone again within a day." src="/assets/img/projects/churn_speelduur_en.png" alt="Bar chart: 44% play one game, 35% stop within a day, 7% within five days and 13% play longer" %}

{% include models.html kicker="Models" title="Three models versus guessing" text="From simple and explainable to powerful." %}

{% include slide.html kicker="Method" title="From raw logs to prediction" text="From the logs we built 13 behavioural features and kept the 8 strongest. All models were tuned and then tested again." src="/assets/img/projects/churn_pipeline_en.svg" alt="Pipeline: timestamp, score and device ID become a churn label and eight features for XGBoost, which gives each new player's chance of returning" full=true %}

{% include slide.html kicker="Results" title="Five times better than guessing" text="All models reach a PR-AUC of 0.37–0.38 (guessing: 0.08). When the model says 'will return', it is right two times out of three." src="/assets/img/projects/churn_modelvergelijking_prauc_en.png" alt="Bar chart: logistic regression, Random Forest and XGBoost reach a PR-AUC of 0.37 to 0.38 versus 0.08 for guessing" %}

{% include slide.html kicker="Evaluation" title="Good at churners, weaker at stayers" text="The models still miss many returners (recall 12–16%). A next step is tuning for recall or trying other time windows." statement=true %}

<div class="role" markdown="1">
## My role
Together with one teammate I did the methodology and analysis: churn definition, features, models and evaluation.
</div>
