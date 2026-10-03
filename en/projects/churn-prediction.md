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
abstract: "From 150,000 games of a mobile game we defined churn ourselves: does a player keep playing after their first five days? Using eight behavioural features, logistic regression, Random Forest and XGBoost predict this almost five times better than guessing. Highest grade of all groups."
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
---

{% include slide.html title="Players quit very quickly" text="44% play only one game and 79% stop within a day. Only 7.9% come back after their first five days." src="/assets/img/projects/churn_spelersretentie.png" alt="Pie chart: 44% play one game, 35% stop within a day, 7% within five days and 13% play longer" %}

{% include slide.html title="What sets stayers apart" text="We built 13 features of early play behaviour from the raw logs; 8 made the cut. Players who quit play shorter and on fewer days." src="/assets/img/projects/churn_effectgrootte_features.png" alt="Horizontal bar chart of the effect size (Cohen's d) of each feature between churners and stayers" %}

{% include slide.html title="Five times better than guessing" text="All three models reach a PR-AUC of 0.37–0.38 versus 0.08 for guessing. XGBoost scores just slightly best." src="/assets/img/projects/churn_modelvergelijking_prauc_en.png" alt="Bar chart: logistic regression, Random Forest and XGBoost reach a PR-AUC of 0.37 to 0.38 versus 0.08 for guessing" %}

{% include slide.html title="Reliable when the model says 'yes'" text="Of the 493 predicted returners, 324 actually return. Honest caveat: recall stays low (12–16%)." src="/assets/img/projects/churn_confusionmatrix_xgboost.png" alt="XGBoost confusion matrix" src2="/assets/img/projects/churn_roc_xgboost.png" alt2="XGBoost ROC curve with an AUC of 0.79" full=true %}

{% include slide.html title="Playing time says the most" text="In all three models, total playing time in the first days is the strongest predictor." src="/assets/img/projects/churn_feature_importance_vergelijking.png" alt="Grouped bar chart of the most important features per model" %}

<div class="role" markdown="1">
## My role
Together with one teammate I did the methodology and analysis: churn definition, feature engineering, model training and evaluation.
</div>
