---
layout: project
lang: nl
ref: citations
project: citations
section: master
title: Voorspellen hoe vaak een wetenschappelijk artikel wordt geciteerd
lead: "Kun je uit titel, samenvatting, auteurs, tijdschrift en jaar voorspellen hoe vaak een artikel geciteerd wordt?"
description: Een NLP- en regressiepipeline (TF-IDF, Sentence-BERT, Ridge) die het aantal citaties voorspelt. Top 5 van het vak Machine Learning.
abstract: "Een reproduceerbare NLP- en regressiepipeline op ruim 2 GB aan wetenschappelijke artikelen. Tekst wordt omgezet met TF-IDF en Sentence-BERT, aangevuld met metadata, en een Ridge-regressie voorspelt het aantal citaties. Het model eindigde in de top 5 van het vak."
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
  - name: "Lineaire regressie, Lasso en Ridge"
    tag: "lineair"
    text: "Tellen de features op met een gewicht. Ridge en Lasso straffen te grote gewichten af, wat helpt bij duizenden tekstfeatures."
  - name: "Random Forest en LightGBM"
    tag: "bomen"
    text: "Combineren veel beslisbomen en kunnen ingewikkelde verbanden leren, maar zijn zwaarder en gevoeliger voor ruis."
  - name: "Ridge op de beste features"
    tag: "gekozen"
    own: true
    text: "Won van alle andere combinaties: een eenvoudig model op goed gekozen features."
---

{% include slide.html kicker="Probleem" title="Welk artikel krijgt impact?" text="Citaties zijn de maat voor wetenschappelijke impact, maar ze stapelen zich pas na jaren op. Kun je bij publicatie al inschatten hoe vaak een artikel geciteerd gaat worden, alleen uit de titel, samenvatting, auteurs, het tijdschrift en het jaar?" %}

{% include slide.html kicker="Data" title="Ruim 2 GB aan artikelen" text="Per artikel: titel, samenvatting, auteurs, venue, jaar, referenties en het aantal citaties. Dat aantal is extreem scheef verdeeld: de meeste artikelen worden weinig geciteerd, een paar heel vaak. Daarom voorspelt het model de wortel ervan." %}

{% include slide.html kicker="Data" title="Van tekst naar getallen" text="Een model rekent met getallen, dus tekst moet eerst worden omgezet. TF-IDF telt welke woorden kenmerkend zijn, Sentence-BERT vat de betekenis van de titel samen in een vector." src="/assets/img/projects/citaties_pipeline.svg" alt="Schema: titel, samenvatting, auteurs, tijdschrift en jaar worden via TF-IDF, Sentence-BERT en metadata omgezet naar features voor een Ridge-regressie" full=true %}

{% include models.html kicker="Modellen" title="Eenvoudig tegen complex" text="Tientallen combinaties van features en modellen vergeleken op een aparte validatieset." %}

{% include slide.html kicker="Methode" title="Eén reproduceerbare pipeline" text="De hele keten, van installatie en embeddings tot training en voorspellingen, draait met één script." src="/assets/img/projects/citaties_methode.svg" alt="Methodeschema in zes stappen: data, tekst opschonen, features, doelvariabele, modellen en evaluatie" full=true %}

{% include slide.html kicker="Resultaten" title="Top 5 van het vak" text="De voorspellingen zijn ingediend op een klassement waarbij de docenten de echte citaties beheerden. Mijn model eindigde bij de vijf beste van alle studenten." statement=true %}

{% include slide.html kicker="Evaluatie" title="Wat werkte, en wat niet" text="Samenvatting, titel, auteurs, venue, decennium en de citaties van referenties droegen het meest bij. Extra features zoals h-index en ervaring van de eerste auteur, en zwaardere boommodellen, verbeterden het resultaat niet." %}

<div class="role" markdown="1">
## Mijn rol
Individueel project: van tekstverwerking en feature engineering tot modelselectie en de pipeline.
</div>
