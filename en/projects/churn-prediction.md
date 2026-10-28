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
abstract: |
  <div style="display:grid; grid-template-columns:repeat(auto-fit, minmax(230px, 1fr)); gap:18px 28px;">
  <div><h3 style="margin:0 0 6px;">The problem</h3><p style="margin:0; font-size:.95rem; line-height:1.5;"><em>Dodge the Mud</em> is a mobile game. Using raw play data (games described by player ID, timestamp and score) we had to predict which players would quit.</p></div>
  <div><h3 style="margin:0 0 6px;">Our solution</h3><p style="margin:0; font-size:.95rem; line-height:1.5;">With no clear signal like cancelling a subscription, we had to define churn ourselves: no game in the twelve days after a five-day observation period (92% of players). From the raw data we built 13 behavioural features, kept 8, and compared logistic regression, Random Forest and eXtreme Gradient Boosting (XGBoost).</p></div>
  <div><h3 style="margin:0 0 6px;">Result</h3><p style="margin:0; font-size:.95rem; line-height:1.5;">All three models perform roughly equally well, XGBoost slightly ahead. The Receiver Operating Characteristic – Area Under the Curve (ROC-AUC) is 0.79 (guessing: 0.50). Recall for churners is 99%, but specificity only 16%: few non-churners are recognised. When the model predicts a non-churner, it is right 2 in 3 times (negative predictive value, NPV, 66%).</p></div>
  </div>
# eerder: abstract_image: /assets/img/projects/churn_abstract_en.svg  (concept-figuur, bestand blijft bewaard)
# eerder: abstract_image: /assets/img/projects/churn_resultaten_en.svg  (eigen figuur; terug via git tag churn-eigen-figuren)
abstract_image: /assets/img/projects/churn_mpl_abstract.svg
abstract_alt: "Three panels. Left: from rows to players; one row per game is grouped by player, each player is followed for 5 days and labelled churner (1, 92%) if they do not play in the next 12 days, otherwise non-churner (0, 8%). Middle: ROC-AUC of guessing 0.50, logistic regression 0.793, Random Forest 0.791 and XGBoost 0.791. Right: confusion matrix of XGBoost; 23,745 of 23,914 churners found (recall 99%), 324 of 2,042 non-churners recognised (specificity 16%), and a non-churner prediction is right 2 in 3 times."
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
sample_grouped:
  arrow: "sort by player and time, then group by player"
  caption: "After grouping by player"
  columns: ["Player", "Games", "Lifetime (days)"]
  rows:
    - ["3526…9119", "4", "0.45"]
    - ["3529…8417", "6", "0.01"]
    - ["3565…3967", "3", "7.09"]
    - ["3523…4543", "1", "–"]
  note: "One row per player (25,956 players). Lifetime = last game − first game; players with one game only (44%) have none."
---

{% comment %} eerder: src="/assets/img/projects/churn_speelduur_en.png" (eigen figuur) {% endcomment %}
{% include data-grouped.html kicker="Exploratory data analysis" title="Only a timestamp, a score and an ID" text="*Dodge the Mud* is a free casual mobile game. The raw data is minimal: for each game played only a player ID, a timestamp and a score. To explore it, we first had to group the games by player. When investigating the data, we noticed that it was very skewed: a large share of players (almost 80%) stops within one day. This is a pattern often seen in mobile casual games: players play intensively in their first session and stop shortly afterwards ([Óskarsdóttir et al., 2022](https://doi.org/10.1007/s41109-022-00524-5))." src="/assets/img/projects/churn_mpl_speelduur.png" alt="Bar chart: 44.0% of new players play one game, 35.4% stop within a day, 7.4% within one to five days and 13.3% play longer than five days; 79% stop within one day." %}

{% comment %} eerder: src="/assets/img/projects/churn_speelduur_label_en.svg" (eigen figuur) {% endcomment %}
{% include slide.html kicker="Define churn" title="When has a player churned?" text="After grouping by player, we created the churn labels with two windows (Kim et al., 2017): an observation period (OP), the behaviour the model gets to see, and a churn prediction period (CP), in which the label is decided. A player is a churner = 1 if they play during the OP but not during the CP, otherwise a non-churner = 0.

The log-plot of player lifetime (see figure below) shows two groups: short triers who stop within about 45 minutes, and players who keep playing for days to weeks. We choose the cut-off at the center of this second group: OP = 5 days. We also choose CP = 12 days: a player who takes a normal break should not be labelled a churner. We looked at the breaks between play sessions (gaps longer than 15 minutes) and found that the median break is 19 hours and that 90% of breaks are shorter than 12 days. Someone who stays away longer than that is very likely not coming back. The result is one row per player with a label: 25,956 players, 92% churners and 8% non-churners." src="/assets/img/projects/churn_mpl_lifetime_rows.svg" alt="Left: histogram of the time between first and last game for 14,531 players with more than one game, on a log scale; short triers stop after a few minutes, a second group plays for days to weeks, and a dashed line marks the 5-day observation period. Right: from rows to players; games are grouped by player, followed for 5 days and labelled churner (1, 92%) or non-churner (0, 8%) depending on whether they still play in the next 12 days. Under the histogram, a timeline of three real players: days 0–5 are the observation period, days 5–17 the churn prediction period, and later games are ignored; player A (games only on day 0) and player B (games on days 0–1 and again on day 22) are churners, player C (games up to day 8) is a non-churner. In the diagram, four example players right after labelling, with their first game, whether they played in the churn prediction period and the label: 3526…9119 13 Jan 2015, no, 1; 3529…8417 16 Aug 2015, no, 1; 3564…0804 11 Jul 2015, yes, 0; 3559…4023 15 Aug 2015, yes, 0." full=true %}

{% comment %} eerder: src="/assets/img/projects/churn_kenmerken_en.svg" (eigen figuur) {% endcomment %}
{% include slide.html kicker="Feature engineering" title="From raw data to 13 features" text="Loose timestamps and scores tell a model little. So from each player's first five days we built 13 features, such as play time, number of games, breaks and best score. For each feature we measured how strongly churners and non-churners differ, using the standardised mean difference (SMD). When two features closely resembled each other (correlation above 0.7), we kept only the stronger one. That left 8. With these we trained three models: logistic regression, Random Forest and XGBoost." src="/assets/img/projects/churn_mpl_smd.png" alt="Horizontal bar chart of the effect size |SMD| of the 13 features. Selected: play time 1.04, best score vs. average 0.75, moment of the best score 0.63, share of games under 15 minutes apart 0.61, number of games 0.54, total score 0.44, average break 0.41, highest score 0.31. Dropped because they correlate with a stronger feature: number of days played, longest break, spread of the score, lowest score and average score." full=true %}

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
    <p>We tested each model with stratified 5-fold cross-validation on 25,956 players, so always on players it had not seen (churner = 1, non-churner = 0). ROC-AUC says how well a model orders players by risk: take a random churner and a random non-churner, and every model gives the churner the higher risk in 79% of such pairs (guessing: 50%). The three models are roughly equally good; the difference lies in the non-churners, where XGBoost recognises slightly more.</p>
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
{% include slide.html kicker="Results" title="The results in numbers" text="We tested each model on 25,956 players with stratified 5-fold cross-validation, to make sure it was evaluated on players it had not seen during training.

**ROC-AUC** says how well a model orders players by risk: for each random pair of a churner and a non-churner, every model gives the churner the higher risk 79% of the time (random guessing: 50%). Recall is the share of churners the model recognises, specificity is the share of non-churners it recognises and NPV is how often a non-churner prediction is correct (all at a threshold of 0.5). The three models are roughly equally good; the difference lies in the specificity, where XGBoost is slightly higher." src="/assets/img/projects/churn_mpl_tabel.png" alt="Table: ROC-AUC, recall, specificity and negative predictive value. Guessing 0.50, 92%, 8%, 8%. Logistic regression 0.793, 99.4%, 12.4%, 64%. Random Forest 0.791, 99.4%, 14.1%, 67%. XGBoost 0.791, 99.3%, 15.9%, 66%." full=true %}

{% include slide.html kicker="Results" title="Play time matters most" text="Which features did the models lean on? For all three, play time in the first five days (total_duration_hours) is by far the most important. After that they differ: logistic regression leans on the total score, Random Forest on the average break between games and XGBoost on the number of games. Importance is normalised per model so that it adds up to 1." src="/assets/img/projects/churn_mpl_fi_slide.png" alt="Horizontal grouped bar chart of normalised feature importance for logistic regression, Random Forest and XGBoost. Play time is the most important for all three (0.40, 0.34 and 0.60); then total score for logistic regression, average break for Random Forest and number of games for XGBoost." full=true %}

{% include slide.html kicker="Discussion" title="Finding churners is easy, recognising non-churners is not" text="The recall for churners is 99%, but the specificity is only 12–16%: the model recognises few non-churners. That is due to the skewed distribution. There are far fewer non-churners to learn from, and during training each model makes the average error over all players as small as possible. Because 92% churn, 'churner' almost always gives the smallest error, so at the default threshold of 50% probability the model mostly predicts that. When it does predict a non-churner, it is right 2 times out of 3 (NPV 64–67%, without a model 8%). A next step is choosing other time windows, so non-churners are less rare, giving non-churners more weight or shifting the threshold." %}
