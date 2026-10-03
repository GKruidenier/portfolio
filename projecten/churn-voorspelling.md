---
layout: project
lang: nl
ref: churn
project: churn
section: master
title: Welke spelers haken af? Churn voorspellen in een mobiele game
lead: "Kun je na de eerste dagen al zien of een nieuwe speler blijft of afhaakt?"
description: Churn gedefinieerd uit ruwe speeldata en voorspeld met logistische regressie, Random Forest en XGBoost. Hoogste cijfer van alle groepen.
image: /assets/img/projects/churn_modelvergelijking_prauc.png
abstract: "Uit 150.000 gespeelde potjes van een mobiele game hebben we churn zelf gedefinieerd: speelt iemand na de eerste vijf dagen nog verder? Met acht gedragskenmerken voorspellen logistische regressie, Random Forest en XGBoost dat bijna vijf keer beter dan gokken. Hoogste cijfer van alle groepen."
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

{% include slide.html title="Spelers haken razendsnel af" text="44% speelt maar één potje en 79% stopt binnen een dag. Slechts 7,9% komt na de eerste vijf dagen nog terug." src="/assets/img/projects/churn_spelersretentie.png" alt="Taartdiagram: 44% speelt één potje, 35% stopt binnen een dag, 7% binnen vijf dagen en 13% speelt langer" %}

{% include slide.html title="Wat blijvers onderscheidt" text="Uit de ruwe logs maakten we 13 kenmerken van vroeg speelgedrag; 8 bleven over. Afhakers spelen korter en op minder dagen." src="/assets/img/projects/churn_effectgrootte_features.png" alt="Horizontaal staafdiagram met de effectgrootte (Cohen's d) van elk kenmerk tussen afhakers en blijvers" %}

{% include slide.html title="Vijf keer beter dan gokken" text="Alle drie modellen halen een PR-AUC van 0,37–0,38 tegen 0,08 bij gokken. XGBoost scoort net het best." src="/assets/img/projects/churn_modelvergelijking_prauc.png" alt="Staafdiagram: logistische regressie, Random Forest en XGBoost halen een PR-AUC van 0,37 tot 0,38, tegen 0,08 bij gokken" %}

{% include slide.html title="Betrouwbaar als het model 'ja' zegt" text="Van de 493 voorspelde terugkeerders komen er 324 echt terug. Eerlijke kanttekening: de recall blijft laag (12–16%)." src="/assets/img/projects/churn_confusionmatrix_xgboost.png" alt="Confusion matrix van XGBoost" src2="/assets/img/projects/churn_roc_xgboost.png" alt2="ROC-curve van XGBoost met een AUC van 0,79" full=true %}

{% include slide.html title="Speelduur zegt het meest" text="In alle drie modellen is de totale speelduur in de eerste dagen de sterkste voorspeller." src="/assets/img/projects/churn_feature_importance_vergelijking.png" alt="Gegroepeerd staafdiagram met de belangrijkste kenmerken per model" %}

<div class="role" markdown="1">
## Mijn rol
Samen met één teamgenoot deed ik de methodologie en analyse: churndefinitie, feature engineering, modeltraining en evaluatie.
</div>
