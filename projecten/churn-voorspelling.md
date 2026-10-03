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
models:
  - name: "Gokken"
    tag: "ondergrens"
    text: "Zonder model raad je in 7,9% van de gevallen goed wie terugkomt (PR-AUC 0,08)."
  - name: "Logistische regressie"
    tag: "model"
    text: "Geeft elk kenmerk een vast gewicht en telt die op. Simpel en goed uit te leggen."
  - name: "Random Forest"
    tag: "model"
    text: "Honderden beslisbomen die elk een deel van de data zien en samen stemmen."
  - name: "XGBoost"
    tag: "model"
    text: "Bomen die na elkaar worden gebouwd, waarbij elke boom de fouten van de vorige corrigeert."
---

{% include slide.html kicker="Probleem" title="Wie haakt af, en wanneer weet je dat?" text="Bij gratis mobiele games verdwijnt het merendeel van de nieuwe spelers binnen een dag. Wie vroeg weet welke spelers blijven, kan gericht ingrijpen. Er is alleen geen abonnement dat wordt opgezegd: wat 'afhaken' is, moesten we zelf uit het gedrag afleiden." %}

{% include slide.html kicker="Data" title="Spelers haken razendsnel af" text="153.929 potjes van de game *Dodge the Mud*, elk met alleen een tijdstip, score en apparaat-ID. 44% speelt één potje en 79% stopt binnen een dag. De levensduur van spelers laat een tweede piek zien rond vijf dagen." src="/assets/img/projects/churn_spelersretentie.png" alt="Taartdiagram: 44% speelt één potje, 35% stopt binnen een dag, 7% binnen vijf dagen en 13% speelt langer" src2="/assets/img/projects/churn_levensduur_spelers.png" alt2="Histogrammen van de levensduur van spelers, met een tweede piek rond vijf dagen" full=true %}

{% include models.html kicker="Modellen" title="Drie modellen tegen gokken" text="Drie veelgebruikte modellen voor churn, van eenvoudig en uitlegbaar tot krachtig, vergeleken met wat je zonder model zou halen." %}

{% include slide.html kicker="Methode" title="Van ruwe logs tot betrouwbare voorspelling" text="We volgen elke speler vijf dagen en kijken of die in de twaalf dagen daarna terugkomt. Beide termijnen volgen uit de data. Alle modellen zijn getuned en daarna opnieuw getoetst met een andere seed." src="/assets/img/projects/churn_methode.svg" alt="Methodeschema in zes stappen: ruwe data, churn labelen, features, modellen, tunen en evaluatie" full=true %}

{% include slide.html kicker="Methode" title="Wat blijvers onderscheidt" text="Uit de ruwe logs maakten we 13 kenmerken van vroeg speelgedrag. We hielden de 8 die afhakers en blijvers het best scheiden en niet overlappen." src="/assets/img/projects/churn_effectgrootte_features.png" alt="Horizontaal staafdiagram met de effectgrootte (Cohen's d) van elk kenmerk tussen afhakers en blijvers" %}

{% include slide.html kicker="Resultaten" title="Vijf keer beter dan gokken" text="Alle drie modellen halen een PR-AUC van 0,37–0,38 tegen 0,08 bij gokken. XGBoost scoort net het best, maar de verschillen zijn klein." src="/assets/img/projects/churn_modelvergelijking_prauc.png" alt="Staafdiagram: logistische regressie, Random Forest en XGBoost halen een PR-AUC van 0,37 tot 0,38, tegen 0,08 bij gokken" %}

{% include slide.html kicker="Resultaten" title="Betrouwbaar als het model 'ja' zegt" text="Van de 493 voorspelde terugkeerders komen er 324 echt terug: twee op de drie, tegen 7,9% bij gokken." src="/assets/img/projects/churn_confusionmatrix_xgboost.png" alt="Confusion matrix van XGBoost" src2="/assets/img/projects/churn_roc_xgboost.png" alt2="ROC-curve van XGBoost met een AUC van 0,79" full=true %}

{% include slide.html kicker="Resultaten" title="Speelduur zegt het meest" text="In alle drie modellen is de totale speelduur in de eerste dagen de sterkste voorspeller." src="/assets/img/projects/churn_feature_importance_vergelijking.png" alt="Gegroepeerd staafdiagram met de belangrijkste kenmerken per model" %}

{% include slide.html kicker="Evaluatie" title="Goed in afhakers, minder in blijvers" text="De modellen missen nog veel spelers die wél terugkomen (recall 12–16%). Dat komt vooral door de scheve verdeling die onze definitie oplevert. Een volgende stap is tunen op recall of andere observatievensters proberen." statement=true %}

<div class="role" markdown="1">
## Mijn rol
Samen met één teamgenoot deed ik de methodologie en analyse: churndefinitie, feature engineering, modeltraining en evaluatie. Hoogste cijfer van alle groepen.
</div>
