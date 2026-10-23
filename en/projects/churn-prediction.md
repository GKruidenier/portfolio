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
abstract: "Using the bare play data of the mobile game Dodge the Mud (for each game only a player, a timestamp and a score) we predicted which new players quit. Because players do not cancel a subscription, we defined ourselves when someone has quit: whoever stays away for twelve days after five days of play. That applies to 92% of new players. From the raw data we built 13 behavioural features and used 8 of them. Our three models rank a quitter as riskier than a stayer 8 times out of 10. They find almost all quitters, but recognise few stayers. Highest grade of all groups."
# eerder: abstract_image: /assets/img/projects/churn_abstract_en.svg  (concept-figuur, bestand blijft bewaard)
abstract_image: /assets/img/projects/churn_resultaten_en.svg
abstract_alt: "Results from the report. Left: ROC-AUC and PR-AUC of logistic regression, Random Forest and XGBoost (0.79 and 0.37–0.38) against guessing (0.50 and 0.08). Right: what XGBoost predicts; 99% of quitters found, 16% of stayers recognised, and when it says 'stays' it is right 2 in 3 times"
course: Analysis of Customer Data, autumn 2025
team: Four students (group 5) · highest grade of all groups
tools: [Python, pandas, scikit-learn, XGBoost, Feature engineering, Cross-validation]
stats:
  - value: "92%"
    label: "of new players quit"
  - value: "8 in 10"
    label: "times the model ranks a quitter as riskier than a stayer (guessing: 5 in 10)"
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

{% include data.html kicker="Context and data" title="Only a timestamp, a score and an ID" text="*Dodge the Mud* is a free casual game for phones. If you see early which players are about to quit, you can still adjust the game. The data is bare: for each game played only a player ID, a timestamp and a score. The data is also skewed: a large share of players (almost 80%) stops within one day." src="/assets/img/projects/churn_speelduur_en.png" alt="Bar chart: 44% play one game, 35% stop within a day, 7% within five days and 13% play longer" %}

{% include slide.html kicker="Define churn" title="When has a player quit?" text="Players do not cancel a subscription, so we had to set a logical boundary ourselves. We follow each new player for five days. After one day you know too little to tell brief triers from real players. A second group of players only stops around day five, so five days make that difference visible. If someone does not play a single game in the twelve days after, they have quit; 90% of normal breaks are shorter. **From rows to players:** we grouped all games by player and put them in time order. This turned each player into one row with a label: stayer (8%) or quitter (92%)." src="/assets/img/projects/churn_speelduur_label_en.svg" alt="Left: histogram of the time between first and last game for players with more than one game. A first group of short triers stops after a few minutes, a second group plays for days to weeks; a dashed line marks five days. Right: rows with player, time and score are grouped by player; after following five days we check whether the player still plays in the next twelve days: yes is stayer (8%), no is quitter (92%)." full=true %}

{% include slide.html kicker="Feature engineering" title="From raw data to 13 features" text="Loose timestamps and scores tell a model little. So from each player's first five days we built 13 features, such as play time, number of games, breaks and best score. For each feature we measured how strongly stayers and quitters differ. When two features closely resembled each other (correlation above 0.7), we kept only the stronger one. That left 8. With these we trained three models: logistic regression, Random Forest and XGBoost." src="/assets/img/projects/churn_kenmerken_en.svg" alt="Bar chart of the effect size of 13 features. Selected: play time 1.04, best score vs. average 0.75, moment of the best score 0.63, games close together 0.61, number of games 0.54, total score 0.44, average break 0.41 and highest score 0.31. Dropped because they closely resemble a stronger feature: number of days played, longest break, spread of the score, lowest score and average score." full=true %}

{% include slide.html kicker="Results" title="Much better than guessing, but stayers remain hard" text="We tested each model with 5-fold cross-validation, so always on players the model had not seen. The three models perform almost equally well. **ROC-AUC 0.79:** put a stayer and a quitter side by side, and the model ranks the quitter as riskier 8 times out of 10 (guessing: 5 out of 10). **PR-AUC 0.38:** the most important score, because stayers are rare. That is almost five times better than guessing (0.08). On the right of the figure is what XGBoost, the slightly best model, predicts." src="/assets/img/projects/churn_resultaten_en.svg" alt="Left: ROC-AUC and PR-AUC of logistic regression, Random Forest and XGBoost (0.79 and 0.37–0.38) against guessing (0.50 and 0.08). Right: what XGBoost predicts; 99% of quitters found, 16% of stayers recognised, and when it says 'stays' it is right 2 in 3 times." full=true %}

{% include slide.html kicker="Evaluation" title="Finding quitters is easy, recognising stayers is not" text="The model finds 99% of quitters, but also sees most stayers as quitters: it recognises only 12–16% of them. When the model does say someone will stay, it is right 2 times out of 3 (without a model 8%). A next step is choosing other time windows, so stayers are less rare, or tuning the model specifically for stayers." statement=true %}

<div class="role" markdown="1">
## My role
Together with one teammate I did the methodology and analysis: the definition of quitting, the features, the models and the evaluation.
</div>
