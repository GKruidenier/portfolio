---
layout: project
lang: nl
ref: citations
project: citations
section: master
title: Voorspellen hoe vaak een wetenschappelijk artikel wordt geciteerd
lead: "Kun je uit titel, samenvatting, auteurs, tijdschrift en jaar voorspellen hoe vaak een artikel geciteerd wordt?"
description: Een NLP- en regressiepipeline (TF-IDF, Sentence-BERT, Ridge) die het aantal citaties voorspelt. Top 5 van het vak Machine Learning.
abstract: "Een pipeline die uit titel, samenvatting, auteurs, tijdschrift en jaar voorspelt hoe vaak een wetenschappelijk artikel wordt geciteerd. Een eenvoudig model op goed gekozen kenmerken eindigde in de top 5 van het vak."
abstract_image: /assets/img/projects/citaties_abstract.svg
abstract_alt: "Visuele samenvatting: een artikel wordt omgezet in getallen en een eenvoudige Ridge-regressie voorspelt het aantal citaties; top 5 van het vak"
course: Machine Learning, MSc Data Science and Society
team: Individueel project
tools: [Python, scikit-learn, NLTK, TF-IDF, Sentence-BERT, Ridge, LightGBM, Random Forest]
stats:
  - value: "Top 5"
    label: "van alle modellen in het vak, op het klassement"
  - value: "> 2 GB"
    label: "aan trainingsdata met wetenschappelijke artikelen"
  - value: "1"
    label: "script draait de hele pipeline, van installatie tot voorspelling"
models:
  - name: "Rechte-lijnmodellen"
    tag: "lineair, Lasso, Ridge"
    text: "Tellen de kenmerken op, elk met een gewicht. Ridge remt te grote gewichten af."
  - name: "Boommodellen"
    tag: "Random Forest, LightGBM"
    text: "Veel beslisbomen samen. Krachtiger, maar ook gevoeliger voor ruis."
  - name: "Gekozen: Ridge"
    tag: "eenvoudig model"
    own: true
    text: "Won van alle andere combinaties op artikelen die het model nog niet had gezien."
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

{% include slide.html kicker="Probleem" title="Hoeveel impact krijgt dit artikel?" text="Citaties stapelen zich pas na jaren op. Kun je bij publicatie al inschatten hoe vaak een artikel geciteerd gaat worden?" src="/assets/img/projects/citaties_probleem.svg" alt="Grafiek: na publicatie stapelt het aantal citaties zich jaar na jaar op; op het moment van publicatie is het nog een vraagteken" full=true %}

{% include data.html kicker="Data" title="Tekst en gegevens per artikel" text="Het aantal citaties is extreem scheef verdeeld: de meeste artikelen worden weinig geciteerd, een paar heel vaak." %}

{% include models.html kicker="Modellen" title="Eenvoudig tegen complex" text="Tientallen combinaties van kenmerken en modellen vergeleken op artikelen die het model nog niet had gezien." %}

{% include slide.html kicker="Methode" title="Van tekst naar getallen" text="Een model rekent met getallen. Daarom zette ik de tekst om: welke woorden kenmerkend zijn, en wat de titel betekent (met een taalmodel). Het model voorspelt de wortel van het aantal citaties, zodat de paar extreem vaak geciteerde artikelen niet alles bepalen." src="/assets/img/projects/citaties_pipeline.svg" alt="Pipeline: titel, samenvatting, auteurs, tijdschrift en jaar worden kenmerkende woorden, de betekenis van de titel en gegevens over auteurs en tijdschrift, waarmee een eenvoudig model het aantal citaties voorspelt" full=true %}

{% include slide.html kicker="Resultaten" title="Bij de beste vijf van het vak" text="De docenten hielden de echte aantallen citaties achter de hand en zetten alle voorspellingen op een ranglijst. Mijn model eindigde bij de vijf beste van alle studenten." src="/assets/img/projects/citaties_ranglijst.svg" alt="Illustratie van de ranglijst: de bovenste vijf plaatsen zijn gemarkeerd, mijn model zat in die groep" big="Top 5" %}

{% include slide.html kicker="Evaluatie" title="Simpel wint" text="Een eenvoudig model op goed gekozen kenmerken versloeg de zwaardere boommodellen. Extra kenmerken, zoals de invloed van een auteur (h-index), voegden niets toe." statement=true %}

<div class="role" markdown="1">
## Mijn rol
Individueel project: alle stappen, van tekstverwerking tot de complete pipeline, heb ik zelf uitgevoerd.
</div>
