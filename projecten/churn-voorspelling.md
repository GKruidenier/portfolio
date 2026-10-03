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
    label: beter dan gokken in het vinden van terugkeerders
  - value: "2 op 3"
    label: voorspelde terugkeerders komt echt terug (gokken: 8%)
  - value: "25.956"
    label: nieuwe spelers geanalyseerd
models:
  - name: "Gokken"
    tag: "ondergrens"
    text: "Zonder model zit je maar bij 8% van de spelers goed."
  - name: "Rekenformule"
    tag: "logistische regressie"
    text: "Telt de kenmerken op, elk met een vast gewicht. Eenvoudig en goed uit te leggen."
  - name: "Stemmende beslisbomen"
    tag: "Random Forest"
    text: "Honderden ja/nee-bomen die elk een stem uitbrengen."
  - name: "Lerende beslisbomen"
    tag: "XGBoost"
    own: true
    text: "Bomen die na elkaar worden gebouwd en elk de fouten van de vorige verbeteren."
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

{% include slide.html kicker="Methode" title="Van ruwe logs tot voorspelling" text="Uit de logs maakten we 13 kenmerken van vroeg speelgedrag en hielden de 8 die het meest zeggen. Daarna testten we elk model op spelers die het nog niet had gezien." src="/assets/img/projects/churn_pipeline.svg" alt="Pipeline: tijdstip, score en speler-ID worden een label 'komt terug' en acht gedragskenmerken voor beslisbomen, die per nieuwe speler de kans op terugkeer geven" full=true %}

{% include slide.html kicker="Resultaten" title="2 op de 3 voorspellingen klopt" text="Alle drie de modellen doen het ongeveer even goed en bijna vijf keer beter dan gokken. Zegt ons beste model dat een speler terugkomt, dan klopt dat in 66% van de gevallen; zonder model is dat 8%." src="/assets/img/projects/churn_resultaat.svg" alt="Staafdiagram: gokken 8%, ons beste model 66% van de voorspelde terugkeerders komt echt terug" full=true %}

{% include slide.html kicker="Evaluatie" title="Goed in afhakers, zwakker in blijvers" text="De modellen vinden nog maar een klein deel van alle spelers die terugkomen (12–16%). Een volgende stap is het model daar gericht op afstemmen, of andere tijdvensters proberen." statement=true %}

<div class="role" markdown="1">
## Mijn rol
Samen met één teamgenoot deed ik de methodologie en analyse: de definitie van afhaken, de kenmerken, de modellen en de evaluatie.
</div>
