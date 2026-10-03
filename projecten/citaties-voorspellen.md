---
layout: project
lang: nl
ref: citations
project: citations
section: master
title: Voorspellen hoe vaak een wetenschappelijk artikel wordt geciteerd
lead: Kun je op basis van de titel, samenvatting, auteurs, het tijdschrift en het jaar voorspellen hoe vaak een artikel geciteerd gaat worden?
description: Een NLP- en regressiepipeline (TF-IDF, Sentence-BERT, Ridge) die het aantal citaties voorspelt. Top 5 van het vak Machine Learning.
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

## De vraag

Kun je op basis van de titel, samenvatting, auteurs, het tijdschrift en het jaar voorspellen hoe vaak een wetenschappelijk artikel geciteerd gaat worden?

## De data

Een grote dataset met wetenschappelijke artikelen (de trainingsdata alleen al is ruim 2 GB), met per artikel de titel, samenvatting, auteurs, venue, publicatiejaar, referenties en het aantal citaties. Het aantal citaties is extreem scheef verdeeld: de meeste artikelen worden weinig geciteerd, een klein aantal heel vaak.

## De pipeline

<ol class="pipeline">
  <li><strong>Tekst opschonen</strong>Stopwoorden weg, lemmatiseren met NLTK</li>
  <li><strong>Tekstfeatures</strong>TF-IDF op samenvatting en titel, Sentence-BERT-embeddings van de titel</li>
  <li><strong>Metadata</strong>Auteurs, venue, decennium en gemiddelde citaties van referenties</li>
  <li><strong>Doelvariabele</strong>Wortel van het aantal citaties, tegen de scheve verdeling</li>
  <li><strong>Ridge-regressie</strong>Beste model na tientallen vergeleken combinaties</li>
</ol>

## Aanpak

- **Tekst omzetten naar features.** Samenvattingen en titels opgeschoond (stopwoorden verwijderd, gelemmatiseerd) en omgezet met TF-IDF. Titels daarnaast omgezet naar betekenisvectoren met het taalmodel Sentence-BERT (all-MiniLM-L6-v2).
- **Kenmerken van auteurs en venue.** Auteurs als volledige namen met TF-IDF gecodeerd, plus venue, decennium en het gemiddelde aantal citaties van de artikelen waarnaar een paper verwijst. Ook h-index, ervaring van de eerste auteur en citaties per venue zijn getest.
- **Doelvariabele transformeren.** Vanwege de scheve verdeling voorspelt het model de wortel van het aantal citaties; lineair, logaritmisch en wortel zijn vergeleken.
- **Systematisch vergelijken.** Tientallen combinaties van features en modellen (lineaire regressie, Lasso, Ridge, Random Forest, LightGBM, XGBoost) getest op een aparte validatieset, met de gemiddelde absolute fout (MAE) als maatstaf.
- **Reproduceerbare pipeline.** De hele keten van installatie, embeddings, training en voorspellingen draait met één script.

## Resultaten

- Het beste model was een Ridge-regressie op de combinatie van samenvatting, titel, auteurs, venue, decennium, gemiddelde citaties van referenties en titel-embeddings.
- De voorspellingen zijn ingediend op een klassement, waarbij de docenten de echte citaties van de testset beheerden. **Mijn model eindigde bij de vijf beste modellen van het vak.**
- Opvallend: een eenvoudig lineair model op goed gekozen features versloeg de zwaardere boommodellen zoals LightGBM en Random Forest.

<div class="role" markdown="1">
## Mijn rol
Individueel project: alle stappen, van feature engineering en tekstverwerking tot modelselectie en de reproduceerbare pipeline, heb ik zelf uitgevoerd.
</div>
