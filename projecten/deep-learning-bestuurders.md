---
layout: project
lang: nl
ref: deeplearning
project: deeplearning
section: master
title: Afgeleide bestuurders herkennen met deep learning
lead: Kan een neuraal netwerk aan de hand van een camerabeeld in de auto herkennen in welke toestand een bestuurder is? Dat is de basis van systemen die waarschuwen voor vermoeidheid of afleiding.
description: Een eigen CNN dat zes toestanden van bestuurders herkent met 95% nauwkeurigheid, vergeleken met een baseline en transfer learning (DenseNet121).
image: /assets/img/projects/deeplearning_nauwkeurigheid_vergelijking.png
course: Deep Learning, voorjaar 2025
team: Zes studenten (groep 6) · ik bouwde het beste model
tools: [Python, TensorFlow/Keras, CNN, Optuna, Transfer learning, DenseNet121]
stats:
  - value: "95%"
    label: nauwkeurigheid op de testset (baseline 79%)
  - value: "0,92"
    label: gemiddelde recall (baseline 0,65)
  - value: "6"
    label: toestanden van de bestuurder herkend
---

## De vraag

Kan een neuraal netwerk aan de hand van een camerabeeld in de auto herkennen in welke toestand een bestuurder is? Dat is de basis van systemen die waarschuwen voor vermoeidheid of afleiding achter het stuur.

## De data

De *Driver Inattention Detection*-dataset van Kaggle: grijswaardenbeelden van bestuurders (verkleind naar 72 × 128 pixels) in zes klassen: veilig rijden, gevaarlijk rijden, afgeleid, drinken, slaperig en gapen. De klassen zijn sterk ongelijk verdeeld; drinken en gapen komen veel minder voor dan veilig rijden.

{% include figure.html src="/assets/img/projects/deeplearning_voorbeeldbeelden.png" alt="Raster met voorbeeldbeelden van bestuurders, elk met hun label" caption="Voorbeelden uit de dataset met hun label." photo=true %}

{% include figure.html src="/assets/img/projects/deeplearning_klassenverdeling.png" alt="Staafdiagram van het aantal beelden per klasse" caption="De klassen zijn sterk ongelijk verdeeld." %}

## Aanpak

- **Baseline.** Een eenvoudig CNN met drie convolutielagen haalde 79% op de testset, maar overfitte en verwarde vooral "afgeleid" met "veilig rijden".
- **Voorbewerking getest.** Klassengewichten en data-augmentatie maakten het model slechter, dus zijn die niet gebruikt.
- **Hyperparameter-tuning met Optuna.** Gezocht over aantal filters, kernelgrootte, dense units, learning rate, optimizer en activatiefunctie, daarna verfijnd met een tweede zoekronde rond de beste instellingen.
- **Architectuur verbeterd.** L2-regularisatie hielp niet; meer dropout wel. De doorslag gaf een netwerk waarin het aantal filters per laag verdubbelt (vanaf 32): naarmate het beeld door max-pooling kleiner wordt, krijgt het netwerk meer kanalen om kenmerken in op te slaan.
- **Transfer learning.** Een voorgetraind DenseNet121 met eigen classificatielagen en een learning-rate-scheduler, als vergelijking met het eigen model.

## Resultaten

{% include figure.html src="/assets/img/projects/deeplearning_nauwkeurigheid_vergelijking.png" alt="Staafdiagram van de testnauwkeurigheid: baseline 79%, DenseNet121 84%, eigen CNN 95%" caption="Baseline, transfer learning en het eigen model vergeleken op de testset." %}

- **Het eigen geoptimaliseerde CNN haalt 95% nauwkeurigheid op de testset**, tegen 79% voor de baseline. De gemiddelde recall steeg van 0,65 naar 0,92.
- Het voorgetrainde DenseNet121 bleef steken op 84%: de voorgetrainde kenmerken pasten minder goed bij deze kleine grijswaardenbeelden.
- "Afgeleid" en "veilig rijden" blijven het lastigste paar, maar het aantal fouten daartussen is sterk gedaald.
- In het rapport zijn ook de ethische kanten besproken: bias in de trainingsdata, privacy bij cameratoezicht in de auto en kwetsbaarheid voor manipulatie.

{% include figure.html src="/assets/img/projects/deeplearning_leercurve_beste_model.png" alt="Lijngrafiek van training- en validatienauwkeurigheid per epoch" caption="Training- en validatienauwkeurigheid van het beste model: de twee lijnen blijven dicht bij elkaar, dus weinig overfitting." %}

<div class="figure-pair">
{% include figure.html src="/assets/img/projects/deeplearning_confusionmatrix_beste_model.png" alt="Confusion matrix van het beste model op de testset" caption="Confusion matrix op de testset." %}
{% include figure.html src="/assets/img/projects/deeplearning_roc_beste_model.png" alt="ROC-curves per klasse met AUC tussen 0,97 en 1,00" caption="ROC-curves per klasse: AUC tussen 0,97 en 1,00." %}
</div>

<div class="role" markdown="1">
## Mijn rol
Ik heb het best presterende model gebouwd: de tweede Optuna-zoekronde, de keuze voor dropout boven L2-regularisatie en de architectuur met verdubbelende filters. Daarnaast heb ik de beelden voorbewerkt voor het DenseNet121-transfermodel en daar de experimenten mee gedaan (inclusief de learning-rate-scheduler), en meegeschreven aan de methodesectie.
</div>
