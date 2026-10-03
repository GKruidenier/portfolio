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
---

{% include slide.html title="De pipeline" text="Tekst en metadata worden features. Een Ridge-regressie voorspelt de wortel van het aantal citaties, tegen de scheve verdeling. Eén script draait alles." src="/assets/img/projects/citaties_pipeline.svg" alt="Schema: titel, samenvatting, auteurs, tijdschrift en jaar worden via TF-IDF, Sentence-BERT en metadata omgezet naar features voor een Ridge-regressie" full=true %}

{% include slide.html title="Simpel wint" text="Na tientallen vergeleken combinaties versloeg een lineair model op goed gekozen features LightGBM en Random Forest. Top 5 van alle modellen in het vak." statement=true %}

<div class="role" markdown="1">
## Mijn rol
Individueel project: van tekstverwerking en feature engineering tot modelselectie en de pipeline.
</div>
