---
layout: project
lang: nl
ref: recommender
project: recommender
section: master
title: Filmaanbevelingen op basis van 27 miljoen beoordelingen
lead: Hoe goed kun je voorspellen welk cijfer iemand geeft aan een film die hij nog niet heeft gezien? Dat is de kern van elk aanbevelingssysteem, van Netflix tot een webshop.
description: Een aanbevelingssysteem op de MovieLens-data met KNNBaseline en SVD, getuned en gevalideerd. RMSE 0,803.
image: /assets/img/projects/recommender_rmse_vergelijking.png
course: Analysis of Customer Data, mei 2025
team: Drie studenten (groep 9)
tools: [Python, pandas, Surprise, Collaborative filtering, KNN, SVD, Hyperparameter-tuning]
stats:
  - value: "0,803"
    label: RMSE van de getunede SVD
  - value: "27 mln"
    label: beoordelingen in de volledige dataset
  - value: "99%"
    label: gelijke verdeling na slim verkleinen
---

## De vraag

Hoe goed kun je voorspellen welk cijfer een gebruiker aan een film geeft die hij nog niet heeft gezien? Dat is de kern van elk aanbevelingssysteem, van Netflix tot een webshop.

## De data

De MovieLens-dataset: meer dan 27 miljoen beoordelingen (0,5 tot 5 sterren) van 283.228 gebruikers voor 53.889 films. De data is extreem scheef: een kleine groep zeer actieve gebruikers geeft het merendeel van de beoordelingen (één gebruiker gaf er 23.715), terwijl de helft van de films minder dan 7 beoordelingen heeft.

<div class="figure-pair">
{% include figure.html src="/assets/img/projects/recommender_verdeling_beoordelingen.png" alt="Staafdiagram van de verdeling van beoordelingen; 4 sterren komt het vaakst voor" caption="Hoe gebruikers films beoordelen: 4 sterren komt het vaakst voor." %}
{% include figure.html src="/assets/img/projects/recommender_beoordelingen_per_gebruiker.png" alt="Verdeling van het aantal beoordelingen per gebruiker" caption="De scheve verdeling van activiteit per gebruiker." %}
</div>

## Aanpak

- **Slim verkleinen zonder informatie te verliezen.** Met de volledige dataset liepen de modellen vast op geheugen. We hebben daarom de 4.000 meest beoordeelde films en 40.000 actiefste gebruikers geselecteerd en daaruit een gestratificeerde steekproef van 3,1 miljoen beoordelingen getrokken. De verdeling van de cijfers bleef daarbij voor 99% gelijk aan het origineel.
- **Drie modellen vergelijken.** Een willekeurige voorspeller als ondergrens (NormalPredictor), een buurmethode op basis van vergelijkbare films (KNNBaseline) en matrixfactorisatie (SVD).
- **Tunen en controleren.** Hyperparameters gezocht met een randomized search gevolgd door een grid search, met 5-voudige cross-validatie. Daarna opnieuw gevalideerd met een andere random seed om te controleren dat de resultaten stabiel zijn.

## Resultaten

{% include figure.html src="/assets/img/projects/recommender_rmse_vergelijking.png" alt="Staafdiagram van de RMSE per model, voor en na tuning" caption="De modellen vergeleken, voor en na tuning. Lager is beter." %}

- **De getunede SVD is het nauwkeurigst, met een RMSE van 0,803.** Gemiddeld zit de voorspelling dus minder dan één ster naast het echte cijfer. De willekeurige baseline zat er 1,43 sterren naast.
- KNNBaseline komt dicht in de buurt (0,814) en is beter uit te leggen, maar schaalt slecht: de gebruikersvariant liep vast op geheugen, dus zijn we overgestapt op vergelijkingen tussen films.
- Met een andere seed veranderde de RMSE maar 0,0002, dus de gevonden instellingen zijn robuust.

> **Advies:** kies KNN als uitlegbaarheid telt en de dataset beperkt is, en SVD als nauwkeurigheid en schaal belangrijker zijn.

<div class="role" markdown="1">
## Mijn rol
Ik heb het grootste deel van dit project uitgevoerd: de data-exploratie, het verkleinen van de dataset, het configureren en tunen van de modellen en de validatie en evaluatie van de resultaten.
</div>
