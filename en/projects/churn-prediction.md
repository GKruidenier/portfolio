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
models:
  - name: "Guessing"
    tag: "lower bound"
    text: "Without a model you would pick the right returners 7.9% of the time (PR-AUC 0.08)."
  - name: "Logistic regression"
    tag: "model"
    text: "Gives each feature a fixed weight and adds them up. Simple and easy to explain."
  - name: "Random Forest"
    tag: "model"
    text: "Hundreds of decision trees that each see part of the data and vote together."
  - name: "XGBoost"
    tag: "model"
    text: "Trees built one after another, each correcting the mistakes of the previous one."
---

{% include slide.html kicker="Problem" title="Who will quit, and when do you know?" text="In free mobile games most new players disappear within a day. Knowing early which players will stay lets a company step in. But there is no subscription to cancel: we had to derive what 'quitting' means from behaviour." %}

{% include slide.html kicker="Data" title="Players quit very quickly" text="153,929 games of *Dodge the Mud*, each with only a timestamp, score and device ID. 44% play one game and 79% stop within a day. Player lifetimes show a second peak around five days." src="/assets/img/projects/churn_spelersretentie.png" alt="Pie chart: 44% play one game, 35% stop within a day, 7% within five days and 13% play longer" src2="/assets/img/projects/churn_levensduur_spelers.png" alt2="Histograms of player lifetime, with a second peak around five days" full=true %}

{% include models.html kicker="Models" title="Three models versus guessing" text="Three common churn models, from simple and explainable to powerful, compared with what you would get without a model." %}

{% include slide.html kicker="Method" title="From raw logs to a reliable prediction" text="We follow each player for five days and check whether they come back in the twelve days after. Both windows come from the data. All models were tuned and then re-tested with another seed." src="/assets/img/projects/churn_methode_en.svg" alt="Six-step method diagram: raw data, labelling churn, features, models, tuning and evaluation" full=true %}

{% include slide.html kicker="Method" title="What sets stayers apart" text="We built 13 features of early play behaviour from the raw logs and kept the 8 that best separate churners from stayers without overlapping." src="/assets/img/projects/churn_effectgrootte_features.png" alt="Horizontal bar chart of the effect size (Cohen's d) of each feature between churners and stayers" %}

{% include slide.html kicker="Results" title="Five times better than guessing" text="All three models reach a PR-AUC of 0.37–0.38 versus 0.08 for guessing. XGBoost scores slightly best, but the differences are small." src="/assets/img/projects/churn_modelvergelijking_prauc_en.png" alt="Bar chart: logistic regression, Random Forest and XGBoost reach a PR-AUC of 0.37 to 0.38 versus 0.08 for guessing" %}

{% include slide.html kicker="Results" title="Reliable when the model says 'yes'" text="Of the 493 predicted returners, 324 actually return: two in three, versus 7.9% when guessing." src="/assets/img/projects/churn_confusionmatrix_xgboost.png" alt="XGBoost confusion matrix" src2="/assets/img/projects/churn_roc_xgboost.png" alt2="XGBoost ROC curve with an AUC of 0.79" full=true %}

{% include slide.html kicker="Results" title="Playing time says the most" text="In all three models, total playing time in the first days is the strongest predictor." src="/assets/img/projects/churn_feature_importance_vergelijking.png" alt="Grouped bar chart of the most important features per model" %}

{% include slide.html kicker="Evaluation" title="Good at churners, weaker at stayers" text="The models still miss many players who do come back (recall 12–16%), mostly because of the imbalance our definition creates. A next step is tuning for recall or trying other observation windows." statement=true %}

<div class="role" markdown="1">
## My role
Together with one teammate I did the methodology and analysis: churn definition, feature engineering, model training and evaluation. Highest grade of all groups.
</div>
