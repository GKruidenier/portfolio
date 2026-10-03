---
layout: project
lang: nl
ref: recommender
project: recommender
section: master
title: Filmaanbevelingen op basis van 27 miljoen beoordelingen
lead: "Hoe goed kun je voorspellen welk cijfer iemand geeft aan een film die hij nog niet heeft gezien?"
description: Een aanbevelingssysteem op de MovieLens-data met KNNBaseline en SVD, getuned en gevalideerd. RMSE 0,803.
image: /assets/img/projects/recommender_rmse_vergelijking.png
abstract: "Op 27 miljoen MovieLens-beoordelingen vergeleken we een buurmethode (KNN) met matrixfactorisatie (SVD). Na slim verkleinen, tunen en dubbel valideren zit de beste SVD gemiddeld minder dan één ster naast het echte cijfer."
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

{% include slide.html title="Scheve data" text="Eén gebruiker gaf 23.715 beoordelingen, terwijl de helft van de films er minder dan 7 heeft. 4 sterren komt het vaakst voor." src="/assets/img/projects/recommender_verdeling_beoordelingen.png" alt="Staafdiagram van de verdeling van beoordelingen; 4 sterren komt het vaakst voor" src2="/assets/img/projects/recommender_beoordelingen_per_gebruiker.png" alt2="Verdeling van het aantal beoordelingen per gebruiker" full=true %}

{% include slide.html title="Verkleinen zonder te verliezen" text="De volledige data paste niet in het geheugen. Een gestratificeerde steekproef van 3,1 miljoen beoordelingen behield 99% van de verdeling." statement=true %}

{% include slide.html title="SVD wint" text="De getunede SVD haalt een RMSE van **0,803**. KNN volgt met 0,814 en is beter uit te leggen, maar schaalt slecht." src="/assets/img/projects/recommender_rmse_vergelijking.png" alt="Staafdiagram van de RMSE per model, voor en na tuning" %}

<div class="role" markdown="1">
## Mijn rol
Ik deed het grootste deel: data-exploratie, het verkleinen van de dataset, het tunen van de modellen en de validatie.
</div>
