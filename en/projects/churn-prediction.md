---
layout: project
lang: en
ref: churn
project: churn
section: master
title: Which players will quit? Predicting churn in a mobile game
lead: "Can you tell after the first few days whether a new player will stay or quit?"
description: Churn defined from raw play logs and predicted with logistic regression, Random Forest and XGBoost. Highest grade of all groups.
image: /assets/img/projects/churn_abstract.png
abstract: "Using the bare play data of the mobile game Dodge the Mud (for each game only a player, a timestamp and a score) we predicted which new players quit. Because players do not cancel a subscription, we defined ourselves when someone has quit: whoever stays away for twelve days after five days of play. That applies to 92% of new players. From the raw data we built 13 behavioural features, used 8 of them, and compared three models: logistic regression, Random Forest and XGBoost. They perform roughly equally well, with XGBoost slightly ahead. Put a quitter and a stayer side by side, and the model gives the quitter the higher risk 8 times out of 10 (guessing: 5 out of 10). It finds 99% of quitters, but recognises only 16% of stayers, because stayers are so rare. When the model does say someone will stay, it is right 2 times out of 3. Highest grade of all groups."
# eerder: abstract_image: /assets/img/projects/churn_abstract_en.svg  (concept-figuur, bestand blijft bewaard)
# eerder: abstract_image: /assets/img/projects/churn_resultaten_en.svg  (eigen figuur; terug via git tag churn-eigen-figuren)
abstract_image: /assets/img/projects/churn_nb_confusion.png
abstract_alt: "Confusion matrices from the notebook for logistic regression, Random Forest and XGBoost. XGBoost correctly predicts 23,745 of the 23,914 quitters and 324 of the 2,042 stayers."
course: Analysis of Customer Data, autumn 2025
team: Four students (group 5) · highest grade of all groups
tools: [Python, pandas, scikit-learn, XGBoost, Feature engineering, Cross-validation]
stats:
  - value: "92%"
    label: "of new players quit"
  - value: "8 in 10"
    label: "pairs of a quitter and a stayer: the quitter gets the higher risk (guessing: 5 in 10)"
  - value: "25,956"
    label: "new players analysed"
models:
  - name: "Guessing"
    tag: "lower bound"
    text: "A coin flip: the quitter gets the higher risk only half of the time."
  - name: "Formula"
    tag: "logistic regression"
    text: "Adds up the features, each with a fixed weight. Simple and easy to explain."
  - name: "Voting decision trees"
    tag: "Random Forest"
    text: "Hundreds of yes/no trees that each cast a vote."
  - name: "Learning decision trees"
    tag: "XGBoost"
    own: true
    text: "Trees built one after another, each fixing the mistakes of the previous one."
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

{% comment %} eerder: src="/assets/img/projects/churn_speelduur_en.png" (eigen figuur) {% endcomment %}
{% include data.html kicker="Context and data" title="Only a timestamp, a score and an ID" text="*Dodge the Mud* is a free casual game for phones. If you see early which players are about to quit, you can still adjust the game. The data is bare: for each game played only a player ID, a timestamp and a score. The data is also skewed: a large share of players (almost 80%) stops within one day." src="/assets/img/projects/churn_nb_speelduur_taart.png" alt="Pie chart from the notebook: 44% of players play one game, 35.4% stop within a day, 7.4% within one to five days and 13.3% play longer than five days." %}

{% comment %} eerder: src="/assets/img/projects/churn_speelduur_label_en.svg" (eigen figuur) {% endcomment %}
{% include slide.html kicker="Define churn" title="When has a player quit?" text="Players do not cancel a subscription, so we had to set a logical boundary ourselves. We follow each new player for five days. After one day you know too little to tell brief triers from real players. A second group of players only stops around day five, so five days make that difference visible. If someone does not play a single game in the twelve days after, they have quit; 90% of normal breaks are shorter. **From rows to players:** we grouped all games by player and put them in time order. This turned each player into one row with a label: quitter = 1 (92%) or stayer = 0 (8%)." src="/assets/img/projects/churn_nb_speelduur.png" alt="Chart from the notebook: distribution of the time between first and last game per player, left in days and right on a logarithmic scale. On the right two groups are visible: a peak at a few minutes and a second peak around five days." full=true %}

{% comment %} eerder: src="/assets/img/projects/churn_kenmerken_en.svg" (eigen figuur) {% endcomment %}
{% include slide.html kicker="Feature engineering" title="From raw data to 13 features" text="Loose timestamps and scores tell a model little. So from each player's first five days we built 13 features, such as play time, number of games, breaks and best score. For each feature we measured how strongly stayers and quitters differ. When two features closely resembled each other (correlation above 0.7), we kept only the stronger one. That left 8. With these we trained three models: logistic regression, Random Forest and XGBoost." src="/assets/img/projects/churn_nb_effectgrootte.png" alt="Chart from the notebook: effect size (Cohen's d) of the 13 features between quitters and stayers. Play time has the largest effect (−1.05), average score the smallest (−0.08)." full=true %}

{% comment %} eerder: src="/assets/img/projects/churn_resultaten_en.svg" (eigen figuur) {% endcomment %}
{% include slide.html kicker="Results" title="ROC-AUC: all three 0.79" text="We tested each model with 5-fold cross-validation, so always on players the model had not seen. The ROC-AUC says how well a model orders players by risk: take a random quitter and a random stayer, and every model gives the quitter the higher risk in 79% of such pairs. Guessing gets 50% (the dashed line). The three curves almost overlap: the models are roughly equally good. This is about the ordering, not about how many players are classified correctly; that is on the next slide." src="/assets/img/projects/churn_nb_roc.png" alt="ROC curves of logistic regression, Random Forest and XGBoost with quitter = 1. The three curves almost overlap, all with an AUC of 0.79, well above the diagonal of guessing (0.50)." %}

{% include slide.html kicker="Results" title="XGBoost recognises slightly more stayers" text="At the default threshold of 50% probability, the difference lies in the stayers. XGBoost recognises 16% of stayers, Random Forest 14% and logistic regression 12%. The confusion matrices come from the notebook: 'Non-Churned' means stays, 'Churned' means quits. XGBoost (C) finds 23,745 of the 23,914 quitters and recognises 324 of the 2,042 stayers." src="/assets/img/projects/churn_nb_confusion.png" alt="Confusion matrices from the notebook for logistic regression, Random Forest and XGBoost. XGBoost correctly predicts 23,745 of the 23,914 quitters and 324 of the 2,042 stayers." full=true %}

{% include slide.html kicker="Evaluation" title="Finding quitters is easy, recognising stayers is not" text="The model finds 99% of quitters, but recognises only 12–16% of stayers. That is due to the skewed distribution. There are far fewer stayers to learn from, and during training each model makes the average error over all players as small as possible. Because 92% quit, 'quits' almost always gives the smallest error, so at the default threshold of 50% probability the model mostly predicts that. When it does say someone will stay, it is right 2 times out of 3 (without a model 8%). A next step is choosing other time windows, so stayers are less rare, giving stayers more weight or shifting the threshold." statement=true %}

<div class="role" markdown="1">
## My role
Together with one teammate I did the methodology and analysis: the definition of quitting, the features, the models and the evaluation.
</div>
