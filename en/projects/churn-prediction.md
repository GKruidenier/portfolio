---
layout: project
lang: en
ref: churn
project: churn
section: master
title: Which players will quit? Predicting churn in a mobile game
lead: Can you tell after a player's first few days whether they will keep playing or quit? Knowing this early lets a company step in.
description: Churn defined from raw play logs and predicted with logistic regression, Random Forest and XGBoost. Highest grade of all groups.
image: /assets/img/projects/churn_modelvergelijking_prauc_en.png
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

## The question

Can you tell after a player's first few days whether they will keep playing the casual game *Dodge the Mud* or quit? Knowing this early lets a company step in to keep players.

## The data

153,929 games played, each with only a timestamp, a score and a device ID. Drop-off is extreme: 44% of players play a single game and 79% stop within a day.

{% include figure.html src="/assets/img/projects/churn_spelersretentie.png" alt="Pie chart: 44% play one game, 35% leave within a day, 7% within five days and 13% play longer" caption="How quickly players quit: 44% play a single game." %}

## Approach

- **Defining churn from behaviour.** There is no subscription to cancel, so we defined churn ourselves: we look at a player's first 5 days (observation period) and predict whether they return in the 12 days after that. Both windows are backed by the data: player lifetimes peak around 5 days, and 90% of breaks between sessions are shorter than 12 days.
- **Feature engineering.** From the raw logs we built 13 features of early play behaviour, such as total play time, time between games and score progression. Using effect sizes and a correlation analysis we kept 8 that do not overlap.
- **Comparing models.** Logistic regression, Random Forest and XGBoost, tuned with a randomized search followed by a grid search, using stratified 5-fold cross-validation. A second validation round with a different random seed showed the results are stable.
- **Handling imbalance.** Only 7.9% of the 25,956 players return. SMOTE, over- and undersampling did not help, so we kept the original distribution and focused on PR-AUC.

{% include figure.html src="/assets/img/projects/churn_effectgrootte_features.png" alt="Horizontal bar chart of each feature's effect size (Cohen's d) between churners and returning players" caption="Which features separate churners from returning players (effect size, Cohen's d). Churners play for less time and on fewer days." %}

## Results

{% include figure.html src="/assets/img/projects/churn_modelvergelijking_prauc_en.png" alt="Bar chart: logistic regression, Random Forest and XGBoost reach a PR-AUC of 0.37 to 0.38, against 0.08 for guessing" caption="All three models score almost five times better than guessing." %}

- All three models reach a ROC-AUC of about 0.79 and a PR-AUC of 0.37–0.38, almost five times better than guessing (0.08). XGBoost is slightly ahead.
- **When the model predicts that a player will return, it is right about two times out of three**, against 7.9% when guessing. Positive predictions are rare but reliable.
- Total play time in the first days is the strongest predictor in every model.
- An honest limitation: recall for returning players stays low (12–16%), mainly because of the imbalance our churn definition creates. A next step is to tune for recall or compare shorter and longer windows.

<div class="figure-pair">
{% include figure.html src="/assets/img/projects/churn_confusionmatrix_xgboost.png" alt="Confusion matrix of XGBoost" caption="XGBoost confusion matrix: of the 493 predicted returners, 324 actually return." %}
{% include figure.html src="/assets/img/projects/churn_roc_xgboost.png" alt="ROC curve of XGBoost with an AUC of 0.79" caption="XGBoost ROC curve (AUC 0.79)." %}
</div>

{% include figure.html src="/assets/img/projects/churn_feature_importance_vergelijking.png" alt="Grouped bar chart of the most important features per model" caption="Most important features per model. Total play time comes first everywhere." %}

<div class="role" markdown="1">
## My role
Together with one teammate I was responsible for the methodology and analysis: the churn definition, feature engineering, model training and evaluation. I also worked on the visualisations and the report.
</div>
