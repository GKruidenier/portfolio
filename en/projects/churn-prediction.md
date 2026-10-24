---
layout: project
lang: en
ref: churn
project: churn
section: master
title: Predicting customer churn in a mobile game
lead: "Can you tell after the first few days whether a new player will stay or quit?"
description: Churn defined from raw play logs and predicted with logistic regression, Random Forest and XGBoost.
image: /assets/img/projects/churn_abstract.png
abstract: "Using the raw player data of the mobile game Dodge the Mud (for each game only a player, a timestamp and a score) we predicted which new players quit. Because players do not cancel a subscription, we defined ourselves when someone has quit: whoever stays away for twelve days after five days of play. That applies to 92% of new players. From the raw data we built 13 behavioural features, used 8 of them, and compared three models: logistic regression, Random Forest and eXtreme Gradient Boosting (XGBoost). They perform roughly equally well, with XGBoost slightly ahead. The Receiver Operating Characteristic – Area Under the Curve (ROC-AUC) is 0.79 for all three (guessing: 0.50): put a churner and a non-churner side by side, and the model gives the churner the higher risk in 79% of cases. The recall for churners is 99%, but the specificity is only 16%: the model recognises few non-churners, because they are so rare. Its negative predictive value (NPV) is 66%: when it predicts that a player will not churn, it is right 2 times out of 3."
# eerder: abstract_image: /assets/img/projects/churn_abstract_en.svg  (concept-figuur, bestand blijft bewaard)
# eerder: abstract_image: /assets/img/projects/churn_resultaten_en.svg  (eigen figuur; terug via git tag churn-eigen-figuren)
abstract_image: /assets/img/projects/churn_abstract_resultaten.png
abstract_alt: "Results table and feature importance chart. ROC-AUC: logistic regression 0.793, Random Forest 0.791, XGBoost 0.791 (guessing 0.50). Recall: 99.3–99.4%. Specificity: 12.4%, 14.1% and 15.9% (guessing 8%). Negative predictive value: 64–67% (guessing 8%). Play time (total_duration_hours) is the most important feature for all three models."
course: Analysis of Customer Data, autumn 2025
team: "Four students (group 5). My role: with one teammate I did the methodology and analysis (churn definition, features, models and evaluation)."
tools: [Python, pandas, scikit-learn, XGBoost, Feature engineering, Cross-validation]
models:
  - name: "Guessing"
    tag: "lower bound"
    text: "A coin flip: the churner gets the higher risk only half of the time."
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
{% include data.html kicker="Context and data" title="Only a timestamp, a score and an ID" text="*Dodge the Mud* is a free casual game for phones. If you see early which players are about to quit, you can still adjust the game. The raw data is minimal: for each game played only a player ID, a timestamp and a score. The data is also skewed: a large share of players (almost 80%) stops within one day." src="/assets/img/projects/churn_nb_speelduur_taart.png" alt="Pie chart from the notebook: 44% of players play one game, 35.4% stop within a day, 7.4% within one to five days and 13.3% play longer than five days." %}

{% comment %} eerder: src="/assets/img/projects/churn_speelduur_label_en.svg" (eigen figuur) {% endcomment %}
{% include slide.html kicker="Define churn" title="When has a player quit?" text="Players do not cancel a subscription, so we had to set a logical boundary ourselves. We follow each new player for five days. After one day you know too little to tell brief triers from real players. A second group of players only stops around day five, so five days make that difference visible. If someone does not play a single game in the twelve days after, they have quit; 90% of normal breaks are shorter. **From rows to players:** we grouped all games by player and put them in time order. This turned each player into one row with a label: churner = 1 (92%) or non-churner = 0 (8%)." src="/assets/img/projects/churn_nb_speelduur.png" alt="Chart from the notebook: distribution of the time between first and last game per player, left in days and right on a logarithmic scale. On the right two groups are visible: a peak at a few minutes and a second peak around five days." full=true %}

{% comment %} eerder: src="/assets/img/projects/churn_kenmerken_en.svg" (eigen figuur) {% endcomment %}
{% include slide.html kicker="Feature engineering" title="From raw data to 13 features" text="Loose timestamps and scores tell a model little. So from each player's first five days we built 13 features, such as play time, number of games, breaks and best score. For each feature we measured how strongly churners and non-churners differ, using the standardised mean difference (SMD). When two features closely resembled each other (correlation above 0.7), we kept only the stronger one. That left 8. With these we trained three models: logistic regression, Random Forest and XGBoost." src="/assets/img/projects/churn_nb_effectgrootte.png" alt="Chart from the notebook: effect size (Cohen's d) of the 13 features between churners and non-churners. Play time has the largest effect (−1.05), average score the smallest (−0.08)." full=true %}

{% comment %} eerder: src="/assets/img/projects/churn_resultaten_en.svg" (eigen figuur) {% endcomment %}
{% comment %} verwijderd op verzoek (ROC-curves / confusion matrices); terugzetten = comment weghalen
{% include slide.html kicker="Results" title="ROC-AUC: all three 0.79" text="We tested each model with 5-fold cross-validation, so always on players the model had not seen. The ROC-AUC says how well a model orders players by risk: take a random churner and a random non-churner, and every model gives the churner the higher risk in 79% of such pairs. Guessing gets 50% (the dashed line). The three curves almost overlap: the models are roughly equally good. This is about the ordering, not about how many players are classified correctly; that is on the next slide." src="/assets/img/projects/churn_nb_roc.png" alt="ROC curves of logistic regression, Random Forest and XGBoost with churner = 1. The three curves almost overlap, all with an AUC of 0.79, well above the diagonal of guessing (0.50)." %}
{% endcomment %}

{% comment %} verwijderd op verzoek (ROC-curves / confusion matrices); terugzetten = comment weghalen
{% include slide.html kicker="Results" title="XGBoost recognises slightly more non-churners" text="At the default threshold of 50% probability, the difference lies in the non-churners. XGBoost recognises 16% of non-churners, Random Forest 14% and logistic regression 12%. The confusion matrices come from the notebook: 'Non-Churned' means non-churner, 'Churned' means churner. XGBoost (C) finds 23,745 of the 23,914 churners and recognises 324 of the 2,042 non-churners." src="/assets/img/projects/churn_nb_confusion.png" alt="Confusion matrices from the notebook for logistic regression, Random Forest and XGBoost. XGBoost correctly predicts 23,745 of the 23,914 churners and 324 of the 2,042 non-churners." full=true %}
{% endcomment %}

{% comment %} eerdere HTML-tabel:
<section class="slide slide--full slide--text">
  <div class="slide__text">
    <p class="slide__num"><span class="slide__kicker">Results</span></p>
    <h2>The results in numbers</h2>
    <p>We tested each model with stratified 5-fold cross-validation on 25,956 players, so always on players it had not seen (churner = 1, non-churner = 0). <strong>ROC-AUC</strong> says how well a model orders players by risk: take a random churner and a random non-churner, and every model gives the churner the higher risk in 79% of such pairs (guessing: 50%). The three models are roughly equally good; the difference lies in the non-churners, where XGBoost recognises slightly more.</p>
  </div>
  <figure class="sample">
    <div class="sample__scroll">
      <table>
        <thead><tr><th>Model</th><th>ROC-AUC</th><th>Churners found</th><th>Non-churners recognised</th><th>Right when it says “non-churner”</th></tr></thead>
        <tbody>
          <tr><td>Guessing</td><td>0.50</td><td>92%</td><td>8%</td><td>8%</td></tr>
          <tr><td>Logistic regression</td><td>0.793</td><td>99.4%</td><td>12.4%</td><td>64%</td></tr>
          <tr><td>Random Forest</td><td>0.791</td><td>99.4%</td><td>14.1%</td><td>67%</td></tr>
          <tr><td><strong>XGBoost</strong></td><td>0.791</td><td>99.3%</td><td><strong>15.9%</strong></td><td>66%</td></tr>
        </tbody>
      </table>
    </div>
    <p class="sample__note">Churners found = recall for churners. Non-churners recognised = share of non-churners the model predicts as non-churners. Right when it says “non-churner” = precision for non-churners. Guessing: labelling players at random in the same proportions (92% quit, 8% stay).</p>
  </figure>
</section>
{% endcomment %}
{% include slide.html kicker="Results" title="The results in numbers" text="We tested each model with stratified 5-fold cross-validation on 25,956 players, so always on players it had not seen (churner = 1, non-churner = 0). **ROC-AUC** says how well a model orders players by risk: take a random churner and a random non-churner, and every model gives the churner the higher risk in 79% of such pairs (guessing: 50%). **Recall** is the share of churners the model finds, **specificity** the share of non-churners it recognises and **NPV** how often a non-churner prediction is right, all at a threshold of 0.5. The three models are roughly equally good; the difference lies in the specificity, where XGBoost is slightly higher." src="/assets/img/projects/churn_nb_tabel.png" alt="Table: ROC-AUC, recall, specificity and negative predictive value. Guessing 0.50, 92%, 8%, 8%. Logistic regression 0.793, 99.4%, 12.4%, 64%. Random Forest 0.791, 99.4%, 14.1%, 67%. XGBoost 0.791, 99.3%, 15.9%, 66%." full=true %}

{% include slide.html kicker="Results" title="Play time matters most" text="Which features did the models lean on? For all three, play time in the first five days (total_duration_hours) is by far the most important. After that they differ: logistic regression leans on the total score, Random Forest on the average break between games and XGBoost on the number of games. Importance is normalised per model so that it adds up to 1." src="/assets/img/projects/churn_nb_feature_importance_slide.png" alt="Bar chart from the notebook comparing normalised feature importance of logistic regression, Random Forest and XGBoost. total_duration_hours is the most important for all three (about 0.40, 0.34 and 0.60); then total_score for logistic regression, mean_inter_event_hours for Random Forest and total_events for XGBoost." full=true %}

{% include slide.html kicker="Evaluation" title="Finding churners is easy, recognising non-churners is not" text="The recall for churners is 99%, but the specificity is only 12–16%: the model recognises few non-churners. That is due to the skewed distribution. There are far fewer non-churners to learn from, and during training each model makes the average error over all players as small as possible. Because 92% churn, 'churner' almost always gives the smallest error, so at the default threshold of 50% probability the model mostly predicts that. When it does predict a non-churner, it is right 2 times out of 3 (NPV 64–67%, without a model 8%). A next step is choosing other time windows, so non-churners are less rare, giving non-churners more weight or shifting the threshold." statement=true %}
