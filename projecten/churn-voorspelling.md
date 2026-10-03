---
layout: project
lang: nl
ref: churn
project: churn
section: master
title: Welke spelers haken af? Churn voorspellen in een mobiele game
lead: Kun je na de eerste dagen al voorspellen of een nieuwe speler blijft spelen of afhaakt? Wie dat vroeg weet, kan gericht ingrijpen.
description: Churn gedefinieerd uit ruwe speeldata en voorspeld met logistische regressie, Random Forest en XGBoost. Hoogste cijfer van alle groepen.
image: /assets/img/projects/churn_modelvergelijking_prauc.png
course: Analysis of Customer Data, najaar 2025
team: Vier studenten (groep 5) · hoogste cijfer van alle groepen
tools: [Python, pandas, scikit-learn, XGBoost, Feature engineering, Cross-validatie]
stats:
  - value: "5×"
    label: beter dan gokken (PR-AUC 0,38 tegen 0,08)
  - value: "2 op 3"
    label: voorspelde terugkeerders keert echt terug
  - value: "0,79"
    label: ROC-AUC van het beste model
---

## De vraag

Kun je na de eerste dagen al voorspellen of een nieuwe speler van de casual game *Dodge the Mud* blijft spelen of afhaakt? Wie dat vroeg weet, kan gericht ingrijpen om spelers te behouden.

## De data

153.929 gespeelde potjes, elk met alleen een tijdstempel, een score en een apparaat-ID. De drop-off is extreem: 44% van de spelers speelt maar één potje en 79% stopt binnen een dag.

{% include figure.html src="/assets/img/projects/churn_spelersretentie.png" alt="Taartdiagram: 44% speelt één potje, 35% stopt binnen een dag, 7% binnen vijf dagen en 13% speelt langer" caption="Hoe snel spelers afhaken: 44% speelt maar één potje." %}

## Aanpak

- **Churn definiëren uit gedrag.** Er is geen abonnement dat wordt opgezegd, dus hebben we churn zelf gedefinieerd: we bekijken de eerste 5 dagen van een speler (observatieperiode) en voorspellen of die in de 12 dagen daarna terugkomt. Beide termijnen zijn onderbouwd met de data: de levensduur van spelers piekt rond 5 dagen en 90% van de pauzes tussen sessies is korter dan 12 dagen.
- **Feature engineering.** Uit de ruwe logs hebben we 13 kenmerken van vroeg speelgedrag gemaakt, zoals totale speelduur, tijd tussen potjes en scoreontwikkeling. Met effectgroottes en een correlatieanalyse bleven er 8 over, zonder overlappende informatie.
- **Modellen vergelijken.** Logistische regressie, Random Forest en XGBoost, getuned met een randomized search gevolgd door een grid search, met gestratificeerde 5-voudige cross-validatie. Een tweede validatieronde met een andere random seed liet zien dat de resultaten stabiel zijn.
- **Omgaan met onbalans.** Slechts 7,9% van de 25.956 spelers komt terug. SMOTE, over- en undersampling hielpen niet, dus hebben we de originele verdeling aangehouden en vooral op PR-AUC gestuurd.

{% include figure.html src="/assets/img/projects/churn_effectgrootte_features.png" alt="Horizontaal staafdiagram met de effectgrootte (Cohen's d) van elk kenmerk tussen afhakers en blijvers" caption="Welke kenmerken afhakers en blijvers onderscheiden (effectgrootte, Cohen's d). Afhakers spelen korter en op minder dagen." %}

## Resultaten

{% include figure.html src="/assets/img/projects/churn_modelvergelijking_prauc.png" alt="Staafdiagram: logistische regressie, Random Forest en XGBoost halen een PR-AUC van 0,37 tot 0,38, tegen 0,08 bij gokken" caption="Alle drie modellen scoren bijna vijf keer beter dan gokken." %}

- Alle drie modellen halen een ROC-AUC van ongeveer 0,79 en een PR-AUC van 0,37–0,38, bijna vijf keer beter dan gokken (0,08). XGBoost scoort net het best.
- **Als het model voorspelt dat een speler terugkomt, klopt dat in ongeveer twee derde van de gevallen**, tegenover 7,9% als je gokt. Positieve voorspellingen komen niet vaak voor, maar zijn betrouwbaar.
- Totale speelduur in de eerste dagen is in alle modellen de sterkste voorspeller.
- Eerlijke beperking: de recall voor terugkerende spelers blijft laag (12–16%). Dat komt vooral door de onbalans die onze churndefinitie oplevert. Een vervolgstap is tunen op recall of kortere en langere vensters vergelijken.

<div class="figure-pair">
{% include figure.html src="/assets/img/projects/churn_confusionmatrix_xgboost.png" alt="Confusion matrix van XGBoost" caption="Confusion matrix van XGBoost: van de 493 voorspelde terugkeerders keren er 324 echt terug." %}
{% include figure.html src="/assets/img/projects/churn_roc_xgboost.png" alt="ROC-curve van XGBoost met een AUC van 0,79" caption="ROC-curve van XGBoost (AUC 0,79)." %}
</div>

{% include figure.html src="/assets/img/projects/churn_feature_importance_vergelijking.png" alt="Gegroepeerd staafdiagram met de belangrijkste kenmerken per model" caption="Belangrijkste kenmerken per model. Totale speelduur staat overal bovenaan." %}

<div class="role" markdown="1">
## Mijn rol
Samen met één teamgenoot was ik verantwoordelijk voor de methodologie en de analyse: de churndefinitie, feature engineering, modeltraining en evaluatie. Daarnaast werkte ik mee aan de visualisaties en het rapport.
</div>
