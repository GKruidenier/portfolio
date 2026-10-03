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
abstract: "Een eigen convolutioneel neuraal netwerk herkent uit één camerabeeld zes toestanden van een bestuurder. Door gericht te tunen steeg de nauwkeurigheid van 79% naar 95%, ruim boven een voorgetraind netwerk."
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
models:
  - name: "Baseline-CNN"
    tag: "startpunt"
    text: "Klein netwerk van drie lagen: 79%."
  - name: "Eigen CNN"
    tag: "beste model"
    own: true
    text: "Vier lagen, filters verdubbelen per laag, met dropout."
  - name: "DenseNet121"
    tag: "transfer learning"
    text: "Al getraind op miljoenen foto's, aangepast aan deze taak."
---

{% include slide.html kicker="Probleem" title="Is de bestuurder afgeleid?" text="Afleiding en vermoeidheid veroorzaken veel ongelukken. Kan een model dat zien aan één camerabeeld?" src="/assets/img/projects/deeplearning_voorbeeldbeelden.png" alt="Raster met voorbeeldbeelden van bestuurders, elk met hun label" photo=true %}

{% include slide.html kicker="Data" title="Bijna 15.000 beelden, scheef verdeeld" text="Grijswaardenbeelden van 72 × 128 pixels in zes klassen. Drinken en gapen komen weinig voor." src="/assets/img/projects/deeplearning_klassen.png" alt="Staafdiagram: veilig rijden 6.180 beelden, gevaarlijk rijden 4.642, afgeleid 2.080, slaperig 979, gapen 546 en drinken 428" %}

{% include models.html kicker="Modellen" title="Zelf bouwen of hergebruiken?" text="Een CNN leert zelf patronen in beelden herkennen, van randen tot houdingen." %}

{% include slide.html kicker="Methode" title="Zo kijkt het netwerk" text="Elke laag vat het beeld samen in steeds meer kenmerken. De laatste laag kiest een van de zes toestanden." src="/assets/img/projects/deeplearning_pipeline.svg" alt="Pipeline: een camerabeeld gaat door vier lagen met 32 tot 256 filters en een dense laag, die een van zes toestanden kiest" full=true %}

{% include slide.html kicker="Resultaten" title="Van 79% naar 95%" text="Het eigen CNN verslaat de baseline en DenseNet121 (84%). De gemiddelde recall steeg van 0,65 naar 0,92." src="/assets/img/projects/deeplearning_nauwkeurigheid_vergelijking.png" alt="Staafdiagram van de testnauwkeurigheid: baseline 79%, DenseNet121 84%, eigen CNN 95%" %}

{% include slide.html kicker="Evaluatie" title="Sterk, maar nog niet klaar voor de weg" text="'Afgeleid' en 'veilig rijden' blijven het lastigst uit elkaar te houden. Voor echt gebruik tellen ook bias en privacy mee." statement=true %}

<div class="role" markdown="1">
## Mijn rol
Ik bouwde het beste model: de tweede Optuna-ronde, de keuze voor dropout en de verdubbelende filters. Ook deed ik de DenseNet121-experimenten.
</div>
