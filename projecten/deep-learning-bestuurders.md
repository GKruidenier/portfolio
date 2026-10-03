---
layout: project
lang: nl
ref: deeplearning
project: deeplearning
section: master
title: Afgeleide bestuurders herkennen met deep learning
lead: "Kan een neuraal netwerk aan een camerabeeld zien in welke toestand een bestuurder is?"
description: Een eigen CNN dat zes toestanden van bestuurders herkent met 95% nauwkeurigheid, vergeleken met een baseline en transfer learning (DenseNet121).
image: /assets/img/projects/deeplearning_nauwkeurigheid_vergelijking.png
abstract: "Een eigen convolutioneel neuraal netwerk herkent uit camerabeelden zes toestanden van een bestuurder, van veilig rijden tot gapen. Met Optuna-tuning, meer dropout en een architectuur met verdubbelende filters steeg de nauwkeurigheid van 79% naar 95%, ruim boven transfer learning met DenseNet121."
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

{% include slide.html title="Zes toestanden achter het stuur" text="Grijswaardenbeelden van 72 × 128 pixels: veilig, gevaarlijk, afgeleid, drinken, slaperig en gapen." src="/assets/img/projects/deeplearning_voorbeeldbeelden.png" alt="Raster met voorbeeldbeelden van bestuurders, elk met hun label" photo=true %}

{% include slide.html title="Ongelijk verdeeld" text="Drinken en gapen komen veel minder voor dan veilig rijden. Klassengewichten en augmentatie hielpen niet." src="/assets/img/projects/deeplearning_klassenverdeling.png" alt="Staafdiagram van het aantal beelden per klasse" %}

{% include slide.html title="Van 79% naar 95%" text="Mijn eigen CNN verslaat de baseline en het voorgetrainde DenseNet121 (84%). De gemiddelde recall steeg van 0,65 naar 0,92." src="/assets/img/projects/deeplearning_nauwkeurigheid_vergelijking.png" alt="Staafdiagram van de testnauwkeurigheid: baseline 79%, DenseNet121 84%, eigen CNN 95%" %}

{% include slide.html title="Leert zonder te overfitten" text="Training en validatie blijven dicht bij elkaar. Per klasse ligt de AUC tussen 0,97 en 1,00." src="/assets/img/projects/deeplearning_leercurve_beste_model.png" alt="Lijngrafiek van training- en validatienauwkeurigheid per epoch" src2="/assets/img/projects/deeplearning_roc_beste_model.png" alt2="ROC-curves per klasse met AUC tussen 0,97 en 1,00" full=true %}

<div class="role" markdown="1">
## Mijn rol
Ik bouwde het beste model: de tweede Optuna-ronde, de keuze voor dropout en de architectuur met verdubbelende filters. Ook deed ik de DenseNet121-experimenten.
</div>
