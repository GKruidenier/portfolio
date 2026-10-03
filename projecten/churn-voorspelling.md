---
layout: project
lang: nl
ref: churn
project: churn
section: master
title: Welke spelers haken af? Churn voorspellen in een mobiele game
lead: "Kun je na de eerste dagen al zien of een nieuwe speler blijft of afhaakt?"
description: Churn gedefinieerd uit ruwe speeldata en voorspeld met logistische regressie, Random Forest en XGBoost. Hoogste cijfer van alle groepen.
image: /assets/img/projects/churn_abstract.png
abstract: "Uit 150.000 gespeelde potjes van een mobiele game bepaalden we zelf wanneer een speler is afgehaakt: dat geldt voor 92% van de nieuwe spelers. Met acht gedragskenmerken uit de eerste vijf dagen schatten onze modellen een afhaker in 8 van de 10 gevallen riskanter in dan een blijver. Hoogste cijfer van alle groepen."
abstract_image: /assets/img/projects/churn_abstract.svg
abstract_alt: "Visuele samenvatting: van twaalf nieuwe spelers haken er elf af; het model leest speelduur, aantal potjes en pauzes en schat in 8 van de 10 gevallen de afhaker riskanter in dan een blijver"
course: Analysis of Customer Data, najaar 2025
team: Vier studenten (groep 5) · hoogste cijfer van alle groepen
tools: [Python, pandas, scikit-learn, XGBoost, Feature engineering, Cross-validatie]
stats:
  - value: "92%"
    label: "van de nieuwe spelers haakt af"
  - value: "8 op 10"
    label: "keer schat het model een afhaker riskanter in dan een blijver (gokken: 5 op 10)"
  - value: "25.956"
    label: "nieuwe spelers geanalyseerd"
models:
  - name: "Gokken"
    tag: "ondergrens"
    text: "Een munt opgooien: de afhaker krijgt dan maar in de helft van de gevallen het hoogste risico."
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

{% include data.html kicker="Context en data" title="Alleen een tijdstip, een score en een ID" text="*Dodge the Mud* is een gratis casual game voor de telefoon. Spelers zeggen geen abonnement op, ze stoppen gewoon. Voor de maker is dat belangrijke informatie: veel afhakers wijst op zwakke plekken in het spel, zoals een verkeerde moeilijkheidsgraad of te weinig uitdaging. Wie vroeg ziet wie gaat afhaken, kan nog bijsturen. De data is kaal: per gespeeld potje alleen een speler-ID, een tijdstip en een score. Het patroon is typisch voor zulke games: de meeste nieuwe spelers zijn binnen een dag weer weg." src="/assets/img/projects/churn_speelduur.png" alt="Staafdiagram: 44% speelt één potje, 35% stopt binnen een dag, 7% binnen vijf dagen en 13% speelt langer" %}

{% include slide.html kicker="Probleem" title="Wanneer is een speler afgehaakt?" text="Omdat er niets op te zeggen valt, bepaalden we dat zelf. We volgen een nieuwe speler vijf dagen. Speelt die in de twaalf dagen daarna geen enkel potje, dan is die afgehaakt. **Waarom vijf dagen?** Na één dag weet je te weinig om korte proberders te onderscheiden van echte spelers. Een tweede groep spelers stopt pas rond dag vijf, dus in vijf dagen wordt dat verschil zichtbaar. **Waarom twaalf dagen?** 90% van de pauzes tussen twee speelsessies is korter dan twaalf dagen; meestal is het zo'n 19 uur. Wie langer wegblijft, neemt dus geen gewone pauze. Zo telt 92% van de nieuwe spelers als afhaker." src="/assets/img/projects/churn_probleem.svg" alt="Tijdlijn: drie spelers worden vijf dagen gevolgd; spelers A en B spelen in de twaalf dagen daarna niet meer en zijn afgehaakt, speler C speelt nog" full=true %}

{% include models.html kicker="Modellen" title="Drie modellen tegen gokken" text="Van eenvoudig en uitlegbaar tot krachtig." %}

{% include slide.html kicker="Methode" title="Van ruwe logs tot voorspelling" text="Uit de logs maakten we 13 kenmerken van vroeg speelgedrag en hielden de 8 die het meest zeggen. Daarna testten we elk model op spelers die het nog niet had gezien." src="/assets/img/projects/churn_pipeline.svg" alt="Pipeline: tijdstip, score en speler-ID worden een label 'haakt af' en acht gedragskenmerken voor beslisbomen, die per nieuwe speler de kans op afhaken geven" full=true %}

{% include slide.html kicker="Resultaten" title="8 op de 10 keer de juiste inschatting" text="Zet je een afhaker en een blijver naast elkaar, dan geeft het model de afhaker in 79% van de gevallen het hoogste risico. Gokken haalt 50%. De drie modellen doen het vrijwel even goed." src="/assets/img/projects/churn_resultaat.svg" alt="Staafdiagram: gokken 50%, rekenformule, stemmende en lerende beslisbomen elk 79%" full=true %}

{% include slide.html kicker="Evaluatie" title="Afhakers vinden is makkelijk, blijvers herkennen niet" text="Het model vindt 99% van de afhakers, maar ziet ook de meeste blijvers als afhaker: maar 12–16% van hen herkent het. Zegt het model wél dat iemand blijft, dan klopt dat in 2 van de 3 gevallen (zonder model 8%). Een volgende stap is andere tijdvensters kiezen, zodat blijvers minder zeldzaam zijn, of het model gericht op blijvers afstemmen." statement=true %}

<div class="role" markdown="1">
## Mijn rol
Samen met één teamgenoot deed ik de methodologie en analyse: de definitie van afhaken, de kenmerken, de modellen en de evaluatie.
</div>
