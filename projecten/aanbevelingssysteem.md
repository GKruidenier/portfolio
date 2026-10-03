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
models:
  - name: "NormalPredictor"
    tag: "baseline"
    text: "Gokt een cijfer uit de algemene verdeling, zonder naar gebruiker of film te kijken."
  - name: "KNNBaseline"
    tag: "model"
    text: "Zoekt films die door dezelfde mensen vergelijkbaar worden beoordeeld. Goed uit te leggen, maar zwaar voor het geheugen."
  - name: "SVD"
    tag: "model"
    text: "Vat gebruikers en films samen in verborgen 'smaakfactoren' en voorspelt het cijfer uit hoe goed die bij elkaar passen."
---

{% include slide.html kicker="Probleem" title="Welke film vindt iemand goed?" text="Een streamingdienst wil films aanraden die iemand echt waardeert. Dat komt neer op één vraag: welk cijfer zou deze gebruiker geven aan een film die hij nog niet heeft gezien?" %}

{% include slide.html kicker="Data" title="27 miljoen beoordelingen, heel scheef" text="283.228 gebruikers en 53.889 films. 4 sterren komt het vaakst voor. Eén gebruiker gaf 23.715 beoordelingen, terwijl de helft van de films er minder dan 7 heeft." src="/assets/img/projects/recommender_verdeling_beoordelingen.png" alt="Staafdiagram van de verdeling van beoordelingen; 4 sterren komt het vaakst voor" src2="/assets/img/projects/recommender_beoordelingen_per_gebruiker.png" alt2="Verdeling van het aantal beoordelingen per gebruiker" full=true %}

{% include slide.html kicker="Data" title="Een kleine top krijgt bijna alle aandacht" text="Een klein deel van de films trekt het gros van de beoordelingen. Daarom werkten we met de 4.000 populairste films en 40.000 actiefste gebruikers, en een steekproef van 3,1 miljoen beoordelingen met 99% dezelfde verdeling." src="/assets/img/projects/recommender_long_tail.png" alt="Lijngrafiek: de relatieve frequentie van beoordelingen daalt steil over de populairste films" %}

{% include models.html kicker="Modellen" title="Drie manieren om een cijfer te voorspellen" text="Twee bekende technieken voor aanbevelingssystemen (collaborative filtering), vergeleken met een willekeurige voorspeller." %}

{% include slide.html kicker="Methode" title="Van 27 miljoen rijen tot getuned model" text="Eerst verkennen en verkleinen, daarna tunen met cross-validatie en de beste instellingen nog eens toetsen met een andere seed." src="/assets/img/projects/recommender_methode.svg" alt="Methodeschema in zes stappen: data, verkennen, verkleinen, modellen, tunen en evaluatie" full=true %}

{% include slide.html kicker="Resultaten" title="SVD wint" text="De getunede SVD zit gemiddeld **0,80 ster** naast het echte cijfer, tegen 1,43 bij gokken. KNN volgt met 0,81. Met een andere seed veranderde de fout maar 0,0002." src="/assets/img/projects/recommender_rmse_vergelijking.png" alt="Staafdiagram van de RMSE per model, voor en na tuning" %}

{% include slide.html kicker="Evaluatie" title="Uitleg of schaal?" text="KNN is beter uit te leggen, maar liep vast op geheugen toen we gebruikers vergeleken. SVD is nauwkeuriger en schaalt beter, maar zijn smaakfactoren zijn niet te interpreteren. Ons advies: KNN als uitleg telt, SVD als schaal telt." statement=true %}

<div class="role" markdown="1">
## Mijn rol
Ik deed het grootste deel: data-exploratie, het verkleinen van de dataset, het tunen van de modellen en de validatie.
</div>
