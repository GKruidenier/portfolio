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
abstract: "From 150,000 games of a mobile game we defined ourselves when a player has quit: 92% of new players. Using eight behavioural features from the first five days, our models rank a quitter as riskier than a stayer 8 times out of 10. Highest grade of all groups."
abstract_image: /assets/img/projects/churn_abstract_en.svg
abstract_alt: "Visual summary: eleven in twelve new players quit; the model reads play time, games and breaks and ranks the quitter as riskier than a stayer 8 times out of 10"
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

{% include data.html kicker="Context and data" title="Only a timestamp, a score and an ID" text="*Dodge the Mud* is a free casual game for phones. Players do not cancel a subscription, they simply stop. For the maker that is important information: many quitters point to weak spots in the game, such as the wrong difficulty or too little challenge. If you see early who is about to quit, you can still steer. The data is bare: for each game played only a player ID, a timestamp and a score. The pattern is typical for such games: most new players are gone again within a day." src="/assets/img/projects/churn_speelduur_en.png" alt="Bar chart: 44% play one game, 35% stop within a day, 7% within five days and 13% play longer" %}

{% include slide.html kicker="Problem" title="When has a player quit?" text="Because there is nothing to cancel, we defined it ourselves. We follow a new player for five days. If they do not play a single game in the twelve days after, they have quit. **Why five days?** After one day you know too little to tell brief triers from real players. A second group of players only stops around day five, so five days make that difference visible. **Why twelve days?** 90% of breaks between two play sessions are shorter than twelve days; usually it is about 19 hours. Anyone who stays away longer is not taking a normal break. This way 92% of new players count as quitters." src="/assets/img/projects/churn_probleem_en.svg" alt="Timeline: three players are followed for five days; players A and B do not play in the twelve days after and have quit, player C still plays" full=true %}

{% include models.html kicker="Models" title="Three models versus guessing" text="From simple and explainable to powerful." %}

{% include slide.html kicker="Method" title="From raw logs to prediction" text="From the logs we built 13 features of early play and kept the 8 that say the most. Then we tested each model on players it had not seen." src="/assets/img/projects/churn_pipeline_en.svg" alt="Pipeline: timestamp, score and player ID become a 'quits' label and eight behaviour features for decision trees, which give each new player's chance of quitting" full=true %}

{% include slide.html kicker="Results" title="The right call 8 times out of 10" text="Put a quitter and a stayer side by side, and the model gives the quitter the higher risk 79% of the time. Guessing gets 50%. The three models perform almost equally well." src="/assets/img/projects/churn_resultaat_en.svg" alt="Bar chart: guessing 50%, formula, voting and learning decision trees 79% each" full=true %}

{% include slide.html kicker="Evaluation" title="Finding quitters is easy, recognising stayers is not" text="The model finds 99% of quitters, but also sees most stayers as quitters: it recognises only 12–16% of them. When the model does say someone will stay, it is right 2 times out of 3 (without a model 8%). A next step is choosing other time windows, so stayers are less rare, or tuning the model specifically for stayers." statement=true %}

<div class="role" markdown="1">
## My role
Together with one teammate I did the methodology and analysis: the definition of quitting, the features, the models and the evaluation.
</div>
