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
abstract: "Met de kale speeldata van de mobiele game Dodge the Mud (per potje alleen een speler, een tijdstip en een score) voorspelden we welke nieuwe spelers afhaken. Omdat spelers geen abonnement opzeggen, bepaalden we zelf wanneer iemand is afgehaakt: wie na vijf dagen spelen twaalf dagen wegblijft. Dat geldt voor 92% van de nieuwe spelers. Uit de ruwe data maakten we 13 gedragskenmerken, waarvan we er 8 gebruikten, en we vergeleken drie modellen: logistische regressie, Random Forest en XGBoost. Ze doen het ongeveer even goed, met XGBoost net iets beter. Zet je een afhaker en een blijver naast elkaar, dan geeft het model in 8 van de 10 gevallen de afhaker het hoogste risico (gokken: 5 van de 10). Het vindt 99% van de afhakers, maar herkent maar 16% van de blijvers, omdat blijvers zo zeldzaam zijn. Zegt het model wel dat iemand blijft, dan klopt dat in 2 van de 3 gevallen. Hoogste cijfer van alle groepen."
# eerder: abstract_image: /assets/img/projects/churn_abstract.svg  (concept-figuur, bestand blijft bewaard)
# eerder: abstract_image: /assets/img/projects/churn_resultaten.svg  (eigen figuur; terug via git tag churn-eigen-figuren)
abstract_image: /assets/img/projects/churn_nb_confusion.png
abstract_alt: "Confusion matrices uit het notebook voor logistische regressie, Random Forest en XGBoost. XGBoost voorspelt 23.745 van de 23.914 afhakers goed en 324 van de 2.042 blijvers."
course: Analysis of Customer Data, najaar 2025
team: Vier studenten (groep 5) · hoogste cijfer van alle groepen
tools: [Python, pandas, scikit-learn, XGBoost, Feature engineering, Cross-validatie]
stats:
  - value: "92%"
    label: "van de nieuwe spelers haakt af"
  - value: "8 op 10"
    label: "paren van een afhaker en een blijver: de afhaker krijgt het hoogste risico (gokken: 5 op 10)"
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

{% comment %} eerder: src="/assets/img/projects/churn_speelduur.png" (eigen figuur) {% endcomment %}
{% include data.html kicker="Context en data" title="Alleen een tijdstip, een score en een ID" text="*Dodge the Mud* is een gratis casual game voor de telefoon. Wie vroeg ziet welke spelers gaan afhaken, kan het spel nog bijsturen. De data is kaal: per gespeeld potje alleen een speler-ID, een tijdstip en een score. Ook is de data scheef verdeeld: een groot deel van de spelers (bijna 80%) stopt binnen één dag." src="/assets/img/projects/churn_nb_speelduur_taart.png" alt="Taartdiagram uit het notebook: 44% van de spelers speelt één potje, 35,4% stopt binnen een dag, 7,4% binnen één tot vijf dagen en 13,3% speelt langer dan vijf dagen." %}

{% comment %} eerder: src="/assets/img/projects/churn_speelduur_label.svg" (eigen figuur) {% endcomment %}
{% include slide.html kicker="Definieer churn/afhaken" title="Wanneer is een speler afgehaakt?" text="Spelers zeggen geen abonnement op, dus moesten we zelf een logische grens trekken. We volgen elke nieuwe speler vijf dagen. Na één dag weet je te weinig om korte proberders te onderscheiden van echte spelers. Een tweede groep spelers stopt pas rond dag vijf, dus in vijf dagen wordt dat verschil zichtbaar. Speelt iemand in de twaalf dagen daarna geen potje meer, dan is die afgehaakt; 90% van de gewone pauzes is korter. **Van rijen naar spelers:** we groepeerden alle potjes per speler en zetten ze op volgorde van tijd. Zo werd elke speler één rij met een label: afhaker = 1 (92%) of blijver = 0 (8%)." src="/assets/img/projects/churn_nb_speelduur.png" alt="Grafiek uit het notebook: verdeling van de tijd tussen eerste en laatste potje per speler, links in dagen en rechts op een logaritmische schaal. Rechts zijn twee groepen te zien: een piek bij een paar minuten en een tweede piek rond vijf dagen." full=true %}

{% comment %} eerder: src="/assets/img/projects/churn_kenmerken.svg" (eigen figuur) {% endcomment %}
{% include slide.html kicker="Feature engineering" title="Van ruwe data naar 13 kenmerken" text="Losse tijdstippen en scores zeggen een model weinig. Daarom maakten we uit de eerste vijf dagen van elke speler 13 kenmerken, zoals de speelduur, het aantal potjes, de pauzes en de beste score. Per kenmerk maten we hoe sterk blijvers en afhakers verschillen. Leken twee kenmerken sterk op elkaar (correlatie boven 0,7), dan hielden we alleen het sterkste. Zo bleven er 8 over. Daarmee trainden we drie modellen: logistische regressie, Random Forest en XGBoost." src="/assets/img/projects/churn_nb_effectgrootte.png" alt="Grafiek uit het notebook: effectgrootte (Cohen's d) van de 13 kenmerken tussen afhakers en blijvers. Speelduur heeft het grootste effect (−1,05), gemiddelde score het kleinste (−0,08)." full=true %}

{% comment %} eerder: src="/assets/img/projects/churn_resultaten.svg" (eigen figuur) {% endcomment %}
{% include slide.html kicker="Resultaten" title="ROC-AUC: alle drie 0,79" text="We testten elk model met 5-voudige kruisvalidatie, dus steeds op spelers die het model nog niet had gezien. De ROC-AUC zegt hoe goed een model spelers op volgorde van risico zet: neem je een willekeurige afhaker en een willekeurige blijver, dan geeft elk model in 79% van zulke paren de afhaker het hoogste risico. Gokken haalt 50% (de stippellijn). De drie curves liggen vrijwel op elkaar: de modellen zijn ongeveer even goed. Dit gaat over de volgorde, niet over hoeveel spelers goed worden ingedeeld; dat staat op de volgende slide." src="/assets/img/projects/churn_nb_roc.png" alt="ROC-curves van logistische regressie, Random Forest en XGBoost met afhaker = 1. De drie curves liggen vrijwel op elkaar, alle met een AUC van 0,79, ruim boven de diagonaal van gokken (0,50)." %}

{% include slide.html kicker="Resultaten" title="XGBoost herkent net de meeste blijvers" text="Bij de standaardgrens van 50% kans zit het verschil in de blijvers. XGBoost herkent 16% van de blijvers, Random Forest 14% en logistische regressie 12%. De confusion matrices komen uit het notebook: 'Non-Churned' is blijft, 'Churned' is haakt af. XGBoost (C) vindt 23.745 van de 23.914 afhakers en herkent 324 van de 2.042 blijvers." src="/assets/img/projects/churn_nb_confusion.png" alt="Confusion matrices uit het notebook voor logistische regressie, Random Forest en XGBoost. XGBoost voorspelt 23.745 van de 23.914 afhakers goed en 324 van de 2.042 blijvers." full=true %}

{% include slide.html kicker="Evaluatie" title="Afhakers vinden is makkelijk, blijvers herkennen niet" text="Het model vindt 99% van de afhakers, maar herkent maar 12–16% van de blijvers. Dat komt door de scheve verdeling. Er zijn veel minder blijvers om van te leren, en tijdens het trainen maakt elk model de gemiddelde fout over alle spelers zo klein mogelijk. Omdat 92% afhaakt, levert 'haakt af' bijna altijd de kleinste fout op, dus bij de standaardgrens van 50% kans voorspelt het model meestal dat. Zegt het wél dat iemand blijft, dan klopt dat in 2 van de 3 gevallen (zonder model 8%). Een volgende stap is andere tijdvensters kiezen, zodat blijvers minder zeldzaam zijn, blijvers zwaarder laten meetellen of de grens verschuiven." statement=true %}

<div class="role" markdown="1">
## Mijn rol
Samen met één teamgenoot deed ik de methodologie en analyse: de definitie van afhaken, de kenmerken, de modellen en de evaluatie.
</div>
