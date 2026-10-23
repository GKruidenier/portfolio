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
abstract_image: /assets/img/projects/churn_resultaten.svg
abstract_alt: "Resultaten uit het verslag. Links: hoe vaak logistische regressie, Random Forest en XGBoost in een paar van een afhaker en een blijver de afhaker het hoogste risico geven (alle 79%, gokken 50%; ROC-AUC) en het deel herkende blijvers (12%, 14% en 16%, gokken 8%). Rechts: wat XGBoost voorspelt, met afhaker = 1 en blijver = 0; 99% van de afhakers gevonden, 16% van de blijvers herkend, en zegt het model 'blijft' dan klopt dat 2 op 3 keer"
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

{% include data.html kicker="Context en data" title="Alleen een tijdstip, een score en een ID" text="*Dodge the Mud* is een gratis casual game voor de telefoon. Wie vroeg ziet welke spelers gaan afhaken, kan het spel nog bijsturen. De data is kaal: per gespeeld potje alleen een speler-ID, een tijdstip en een score. Ook is de data scheef verdeeld: een groot deel van de spelers (bijna 80%) stopt binnen één dag." src="/assets/img/projects/churn_speelduur.png" alt="Staafdiagram: 44% speelt één potje, 35% stopt binnen een dag, 7% binnen vijf dagen en 13% speelt langer" %}

{% include slide.html kicker="Definieer churn/afhaken" title="Wanneer is een speler afgehaakt?" text="Spelers zeggen geen abonnement op, dus moesten we zelf een logische grens trekken. We volgen elke nieuwe speler vijf dagen. Na één dag weet je te weinig om korte proberders te onderscheiden van echte spelers. Een tweede groep spelers stopt pas rond dag vijf, dus in vijf dagen wordt dat verschil zichtbaar. Speelt iemand in de twaalf dagen daarna geen potje meer, dan is die afgehaakt; 90% van de gewone pauzes is korter. **Van rijen naar spelers:** we groepeerden alle potjes per speler en zetten ze op volgorde van tijd. Zo werd elke speler één rij met een label: afhaker = 1 (92%) of blijver = 0 (8%)." src="/assets/img/projects/churn_speelduur_label.svg" alt="Links: histogram van de tijd tussen eerste en laatste potje voor spelers met meer dan één potje. Een eerste groep korte proberders stopt na een paar minuten, een tweede groep speelt dagen tot weken; een stippellijn markeert vijf dagen. Rechts: rijen met speler, tijdstip en score worden per speler gegroepeerd; na vijf dagen volgen wordt gekeken of de speler in de twaalf dagen daarna nog speelt: ja is blijver (0, 8%), nee is afhaker (1, 92%)." full=true %}

{% include slide.html kicker="Feature engineering" title="Van ruwe data naar 13 kenmerken" text="Losse tijdstippen en scores zeggen een model weinig. Daarom maakten we uit de eerste vijf dagen van elke speler 13 kenmerken, zoals de speelduur, het aantal potjes, de pauzes en de beste score. Per kenmerk maten we hoe sterk blijvers en afhakers verschillen. Leken twee kenmerken sterk op elkaar (correlatie boven 0,7), dan hielden we alleen het sterkste. Zo bleven er 8 over. Daarmee trainden we drie modellen: logistische regressie, Random Forest en XGBoost." src="/assets/img/projects/churn_kenmerken.svg" alt="Staafdiagram van de effectgrootte van 13 kenmerken. Gekozen: speelduur 1,04, beste score ten opzichte van gemiddelde 0,75, moment van de beste score 0,63, potjes kort na elkaar 0,61, aantal potjes 0,54, totale score 0,44, gemiddelde pauze 0,41 en hoogste score 0,31. Weggelaten omdat ze sterk lijken op een beter kenmerk: aantal speeldagen, langste pauze, spreiding van de score, laagste score en gemiddelde score." full=true %}

{% include slide.html kicker="Resultaten" title="Drie modellen ongeveer even goed, XGBoost net iets beter" text="We testten elk model met 5-voudige kruisvalidatie, dus steeds op spelers die het model nog niet had gezien. **Afhaker boven blijver (79%):** neem je een willekeurige afhaker en een willekeurige blijver, dan geeft elk model in 79% van zulke paren de afhaker het hoogste risico. Gokken haalt 50%. Dit gaat dus over de volgorde, niet over hoeveel spelers goed worden ingedeeld; dat staat rechts in de figuur. In vaktermen is dit de ROC-AUC van 0,79. **Herkende blijvers:** hier zit het verschil. XGBoost herkent 16% van de blijvers, Random Forest 14% en logistische regressie 12%. Rechts in de figuur staat wat XGBoost per speler voorspelt." src="/assets/img/projects/churn_resultaten.svg" alt="Links: hoe vaak logistische regressie, Random Forest en XGBoost in een paar van een afhaker en een blijver de afhaker het hoogste risico geven (alle 79%, gokken 50%; ROC-AUC) en het deel herkende blijvers (12%, 14% en 16%, gokken 8%). Rechts: wat XGBoost voorspelt, met afhaker = 1 en blijver = 0; 99% van de afhakers gevonden, 16% van de blijvers herkend, en zegt het model 'blijft' dan klopt dat 2 op 3 keer." full=true %}

{% include slide.html kicker="Evaluatie" title="Afhakers vinden is makkelijk, blijvers herkennen niet" text="Het model vindt 99% van de afhakers, maar herkent maar 12–16% van de blijvers. Dat komt door de scheve verdeling. Er zijn veel minder blijvers om van te leren, en tijdens het trainen maakt elk model de gemiddelde fout over alle spelers zo klein mogelijk. Omdat 92% afhaakt, levert 'haakt af' bijna altijd de kleinste fout op, dus bij de standaardgrens van 50% kans voorspelt het model meestal dat. Zegt het wél dat iemand blijft, dan klopt dat in 2 van de 3 gevallen (zonder model 8%). Een volgende stap is andere tijdvensters kiezen, zodat blijvers minder zeldzaam zijn, blijvers zwaarder laten meetellen of de grens verschuiven." statement=true %}

<div class="role" markdown="1">
## Mijn rol
Samen met één teamgenoot deed ik de methodologie en analyse: de definitie van afhaken, de kenmerken, de modellen en de evaluatie.
</div>
