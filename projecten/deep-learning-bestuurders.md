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
abstract_image: /assets/img/projects/deeplearning_abstract.svg
abstract_alt: "Visuele samenvatting: een camerabeeld van een bestuurder met telefoon gaat door een eigen neuraal netwerk, dat 'afgeleid' herkent; 95% van de beelden juist, eerste model 79%"
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
  - name: "Eenvoudig netwerk"
    tag: "startpunt"
    text: "Drie lagen. Haalde 79%, maar leerde de oefenbeelden te veel uit het hoofd."
  - name: "Mijn netwerk"
    tag: "eigen ontwerp"
    own: true
    text: "Vier lagen die steeds meer kenmerken leren, met maatregelen tegen uit het hoofd leren."
  - name: "Voorgetraind netwerk"
    tag: "DenseNet121"
    text: "Al getraind op miljoenen foto's en daarna aangepast aan deze taak."
---

{% include slide.html kicker="Probleem" title="Is de bestuurder afgeleid?" text="Afleiding en vermoeidheid veroorzaken veel ongelukken. Kan een model dat zien aan één camerabeeld?" src="/assets/img/projects/deeplearning_voorbeeldbeelden.png" alt="Raster met voorbeeldbeelden van bestuurders, elk met hun label" photo=true %}

{% include slide.html kicker="Data" title="Bijna 15.000 beelden, scheef verdeeld" text="Grijswaardenbeelden van 72 × 128 pixels in zes klassen. Drinken en gapen komen weinig voor." src="/assets/img/projects/deeplearning_klassen.png" alt="Staafdiagram: veilig rijden 6.180 beelden, gevaarlijk rijden 4.642, afgeleid 2.080, slaperig 979, gapen 546 en drinken 428" %}

{% include models.html kicker="Modellen" title="Zelf bouwen of hergebruiken?" text="Een neuraal netwerk voor beelden leert zelf waar het op moet letten, van randen tot houdingen." %}

{% include slide.html kicker="Methode" title="Zo kijkt het netwerk" text="Elke laag vat het beeld samen in steeds meer kenmerken. De laatste laag kiest een van de zes toestanden." src="/assets/img/projects/deeplearning_pipeline.svg" alt="Pipeline: een camerabeeld gaat door vier lagen met steeds meer kenmerken en een besluitlaag, die een van zes toestanden kiest" full=true %}

{% include slide.html kicker="Resultaten" title="Van 79% naar 95%" text="Mijn netwerk herkent 95% van de testbeelden goed, tegen 79% voor het eerste netwerk en 84% voor het voorgetrainde netwerk. Ook de zeldzame toestanden worden veel vaker gevonden (van 65% naar 92%)." src="/assets/img/projects/deeplearning_resultaat.svg" alt="Staafdiagram: eerste netwerk 79%, voorgetraind netwerk 84%, mijn netwerk 95% juist herkend" full=true %}

{% include slide.html kicker="Evaluatie" title="Sterk, maar nog niet klaar voor de weg" text="'Afgeleid' en 'veilig rijden' blijven het lastigst uit elkaar te houden. Voor echt gebruik tellen ook eerlijkheid tussen groepen bestuurders en privacy mee." statement=true %}

<div class="role" markdown="1">
## Mijn rol
Ik bouwde het beste model: de tweede ronde automatische afstemming, de keuze voor dropout en de opbouw met steeds meer kenmerken per laag. Ook deed ik de experimenten met het voorgetrainde netwerk.
</div>
