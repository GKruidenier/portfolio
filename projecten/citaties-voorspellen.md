---
layout: project
lang: nl
ref: citations
project: citations
section: master
title: Voorspellen hoe vaak een wetenschappelijk artikel wordt geciteerd
lead: "Kun je uit titel, samenvatting, auteurs, tijdschrift en jaar voorspellen hoe vaak een artikel geciteerd wordt?"
description: Een NLP- en regressiepipeline (TF-IDF, Sentence-BERT, Ridge) die het aantal citaties voorspelt. Top 5 van het vak Machine Learning.
abstract: "Een reproduceerbare pipeline die uit titel, samenvatting, auteurs, tijdschrift en jaar voorspelt hoe vaak een artikel wordt geciteerd. Een eenvoudige Ridge-regressie op goed gekozen features eindigde in de top 5 van het vak."
course: Machine Learning, MSc Data Science and Society
team: Individueel project
tools: [Python, scikit-learn, NLTK, TF-IDF, Sentence-BERT, Ridge, LightGBM, Random Forest]
stats:
  - value: "Top 5"
    label: van alle modellen in het vak, op het klassement
  - value: "> 2 GB"
    label: aan trainingsdata met wetenschappelijke artikelen
  - value: "1"
    label: script draait de hele pipeline, van installatie tot voorspelling
models:
  - name: "Lineaire modellen"
    tag: "vergeleken"
    text: "Lineaire regressie, Lasso en Ridge: features met een gewicht."
  - name: "Boommodellen"
    tag: "vergeleken"
    text: "Random Forest en LightGBM: veel beslisbomen samen."
  - name: "Ridge"
    tag: "gekozen"
    own: true
    text: "Lineair, met een rem op te grote gewichten."
sample:
  caption: "Zo ziet de data eruit"
  columns: ["Titel", "Tijdschrift", "Jaar", "Citaties"]
  rows:
    - ["Feature-based video mosaic", "ICIP", "2000", "51"]
    - ["Discovery of Frequent Word Sequences in Text", "LNCS", "2002", "15"]
    - ["A Fast Feature-based Dimension Reduction…", "Neural Processing Letters", "2006", "1"]
    - ["A Fully Integrated Humidity Sensor…", "Sensors", "2012", "8"]
  note: "Plus samenvatting, auteurs en referenties per artikel; ruim 2 GB in totaal."
---

{% include slide.html kicker="Probleem" title="Hoeveel impact krijgt dit artikel?" text="Citaties stapelen zich pas na jaren op. Kun je het aantal al bij publicatie voorspellen?" src="/assets/img/projects/citaties_probleem.svg" alt="Schets: een artikel met titel, auteurs, tijdschrift en samenvatting gaat een model in dat het aantal citaties voorspelt" full=true %}

{% include data.html kicker="Data" title="Tekst en metadata per artikel" text="Het aantal citaties is extreem scheef verdeeld: de meeste artikelen worden weinig geciteerd, een paar heel vaak." %}

{% include models.html kicker="Modellen" title="Eenvoudig tegen complex" text="Tientallen combinaties van features en modellen vergeleken op een aparte validatieset." %}

{% include slide.html kicker="Methode" title="Van tekst naar getallen" text="TF-IDF vindt kenmerkende woorden, Sentence-BERT vat de betekenis van de titel samen. Het model voorspelt de wortel van het aantal citaties." src="/assets/img/projects/citaties_pipeline.svg" alt="Pipeline: titel, samenvatting, auteurs, tijdschrift en jaar worden via TF-IDF, Sentence-BERT en metadata features voor een Ridge-regressie" full=true %}

{% include slide.html kicker="Resultaten" title="Bij de beste vijf van het vak" text="Op het klassement van de docenten, die de echte citaties beheerden, eindigde mijn model bij de vijf beste van alle studenten." big="Top 5" %}

{% include slide.html kicker="Evaluatie" title="Simpel wint" text="Een lineair model versloeg de zwaardere boommodellen. Extra features zoals de h-index van auteurs voegden niets toe." statement=true %}

<div class="role" markdown="1">
## Mijn rol
Individueel project: alle stappen, van tekstverwerking tot de pipeline, heb ik zelf uitgevoerd.
</div>
