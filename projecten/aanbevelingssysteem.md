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
abstract: "Op 27 miljoen MovieLens-beoordelingen vergeleken we twee technieken voor aanbevelingen. Na slim verkleinen en afstemmen zit de beste, op basis van smaakprofielen, gemiddeld 0,8 ster naast het echte cijfer, tegen 1,4 bij gokken."
abstract_image: /assets/img/projects/recommender_abstract.svg
abstract_alt: "Visuele samenvatting: een grotendeels leeg raster van kijkers en films; SVD koppelt smaakprofielen en vult het lege vakje in met 4,2 sterren, gemiddeld 0,8 ster naast het echte cijfer"
course: Analysis of Customer Data, mei 2025
team: Drie studenten (groep 9)
tools: [Python, pandas, Surprise, Collaborative filtering, KNN, SVD, Hyperparameter-tuning]
stats:
  - value: "0,8 ★"
    label: gemiddeld ernaast bij een voorspeld cijfer (gokken: 1,4)
  - value: "27 mln"
    label: beoordelingen in de volledige dataset
  - value: "99%"
    label: dezelfde verdeling na slim verkleinen
models:
  - name: "Gokken"
    tag: "NormalPredictor"
    text: "Kiest een willekeurig cijfer uit de algemene verdeling."
  - name: "Vergelijkbare films"
    tag: "KNN"
    text: "Kijkt naar films die dezelfde mensen ook goed of slecht vonden. Goed uit te leggen, maar zwaar voor het geheugen."
  - name: "Smaakprofielen"
    tag: "SVD"
    own: true
    text: "Vat kijkers en films samen in een paar verborgen smaakkenmerken en kijkt hoe goed die bij elkaar passen."
sample:
  caption: "Zo ziet de data eruit"
  columns: ["Kijker", "Film", "Cijfer", "Datum"]
  rows:
    - ["1", "307", "3,5", "27-10-2009"]
    - ["1", "481", "3,5", "27-10-2009"]
    - ["1", "1091", "1,5", "27-10-2009"]
    - ["1", "1257", "4,5", "27-10-2009"]
  note: "Eén rij per beoordeling: 27 miljoen rijen van 283.228 kijkers."
---

{% include slide.html kicker="Probleem" title="Welk cijfer zou je deze film geven?" text="Dat is de kern van elk aanbevelingssysteem: de lege vakjes invullen, zodat je kunt aanraden wat iemand waarschijnlijk goed vindt." src="/assets/img/projects/recommender_probleem.svg" alt="Raster van kijkers en films met ingevulde cijfers en lege vakjes; één leeg vakje wordt voorspeld als 4,2 sterren" full=true %}

{% include data.html kicker="Data" title="27 miljoen beoordelingen" text="Kijkers geven vooral hoge cijfers, en een kleine groep geeft het merendeel ervan." src="/assets/img/projects/recommender_cijfers.png" alt="Staafdiagram van de verdeling van cijfers; 4 sterren komt het vaakst voor" %}

{% include models.html kicker="Modellen" title="Drie manieren om een cijfer te voorspellen" %}

{% include slide.html kicker="Methode" title="Van 27 miljoen naar 3,1 miljoen rijen" text="We hielden de populairste films en actiefste kijkers en trokken een steekproef met 99% dezelfde verdeling. Daarna stemden we de instellingen af en testten we op beoordelingen die het model nog niet had gezien." src="/assets/img/projects/recommender_pipeline.svg" alt="Pipeline: kijker, film en cijfer worden verkleind en gesampled, daarna voorspellen smaakprofielen het cijfer voor een nieuwe film" full=true %}

{% include slide.html kicker="Resultaten" title="Gemiddeld 0,8 ster ernaast" text="Smaakprofielen (SVD) zitten het dichtst bij het echte cijfer, net voor vergelijkbare films (KNN). Gokken zit er 1,4 ster naast. Met een andere willekeurige verdeling bleef het resultaat vrijwel gelijk." src="/assets/img/projects/recommender_resultaat.svg" alt="Staafdiagram: gokken 1,43 ster ernaast, vergelijkbare films 0,81, smaakprofielen 0,80" full=true %}

{% include slide.html kicker="Evaluatie" title="Uitleg of schaal?" text="Vergelijkbare films zijn makkelijker uit te leggen, maar liepen vast op het geheugen. Smaakprofielen zijn nauwkeuriger en schalen beter, maar zijn minder transparant." statement=true %}

<div class="role" markdown="1">
## Mijn rol
Ik deed het grootste deel: data-exploratie, het verkleinen van de data, het afstemmen van de modellen en de validatie.
</div>
