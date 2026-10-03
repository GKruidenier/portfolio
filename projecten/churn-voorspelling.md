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
abstract: "Uit 150.000 gespeelde potjes van een mobiele game definieerden we zelf wanneer een speler afhaakt. Met acht gedragskenmerken voorspellen onze modellen na vijf dagen wie terugkomt, bijna vijf keer beter dan gokken. Hoogste cijfer van alle groepen."
abstract_image: /assets/img/projects/churn_abstract.svg
abstract_alt: "Visuele samenvatting: van twaalf nieuwe spelers komt er één terug; het model leest speelduur, aantal potjes en pauzes en zit bij 'komt terug' in twee op de drie gevallen goed"
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
    text: "Zonder model raak je 7,9% van de terugkeerders."
  - name: "Logistische regressie"
    tag: "model"
    text: "Telt de kenmerken op met een vast gewicht."
  - name: "Random Forest"
    tag: "model"
    text: "Honderden beslisbomen die samen stemmen."
  - name: "XGBoost"
    tag: "model"
    own: true
    text: "Bomen die elkaars fouten stap voor stap verbeteren."
sample:
  caption: "Zo ziet de data eruit"
  columns: ["Speler", "Tijdstip", "Score"]
  rows:
    - ["3526…9119", "13-01-2015 13:54", "0"]
    - ["3526…9119", "13-01-2015 13:55", "7"]
    - ["3526…9119", "13-01-2015 13:55", "6"]
    - ["3526…9119", "14-01-2015 00:38", "252"]
  note: "Eén rij per gespeeld potje: 153.929 rijen, verder niets."
---

{% include slide.html kicker="Probleem" title="Wanneer is een speler afgehaakt?" text="Er is geen abonnement om op te zeggen. We volgen een nieuwe speler vijf dagen en voorspellen of die daarna nog terugkomt." src="/assets/img/projects/churn_probleem.svg" alt="Tijdlijn: drie spelers worden vijf dagen gevolgd; alleen speler C speelt in de twaalf dagen daarna weer en telt als blijver" full=true %}

{% include data.html kicker="Data" title="Alleen een tijdstip, een score en een ID" text="De meeste nieuwe spelers zijn binnen een dag weer weg." src="/assets/img/projects/churn_speelduur.png" alt="Staafdiagram: 44% speelt één potje, 35% stopt binnen een dag, 7% binnen vijf dagen en 13% speelt langer" %}

{% include models.html kicker="Modellen" title="Drie modellen tegen gokken" text="Van eenvoudig en uitlegbaar tot krachtig." %}

{% include slide.html kicker="Methode" title="Van ruwe logs tot voorspelling" text="Uit de logs maakten we 13 gedragskenmerken en hielden de 8 sterkste. Alle modellen zijn getuned en daarna opnieuw getoetst." src="/assets/img/projects/churn_pipeline.svg" alt="Pipeline: tijdstip, score en apparaat-ID worden een churn-label en acht kenmerken voor XGBoost, dat per nieuwe speler de kans op terugkeer geeft" full=true %}

{% include slide.html kicker="Resultaten" title="Vijf keer beter dan gokken" text="Alle modellen halen een PR-AUC van 0,37–0,38 (gokken: 0,08). Zegt het model 'komt terug', dan klopt dat in twee op de drie gevallen." src="/assets/img/projects/churn_modelvergelijking_prauc.png" alt="Staafdiagram: logistische regressie, Random Forest en XGBoost halen een PR-AUC van 0,37 tot 0,38, tegen 0,08 bij gokken" %}

{% include slide.html kicker="Evaluatie" title="Goed in afhakers, zwakker in blijvers" text="De modellen missen nog veel terugkeerders (recall 12–16%). Een volgende stap is tunen op recall of andere tijdvensters proberen." statement=true %}

<div class="role" markdown="1">
## Mijn rol
Samen met één teamgenoot deed ik de methodologie en analyse: churndefinitie, kenmerken, modellen en evaluatie.
</div>
