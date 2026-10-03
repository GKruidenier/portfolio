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
models:
  - name: "Baseline-CNN"
    tag: "startpunt"
    text: "Een klein netwerk met drie lagen van elk 8 filters. Haalde 79%, maar leerde de trainingsdata te veel uit het hoofd."
  - name: "Eigen CNN"
    tag: "beste model"
    own: true
    text: "Vier lagen waarbij het aantal filters per laag verdubbelt (32 tot 256), met batchnormalisatie en dropout tegen overfitting."
  - name: "DenseNet121"
    tag: "transfer learning"
    text: "Een netwerk dat al op miljoenen foto's is getraind, met eigen lagen erop voor deze zes klassen."
---

{% include slide.html kicker="Probleem" title="Kan een camera zien hoe de bestuurder erbij zit?" text="Afleiding en vermoeidheid achter het stuur veroorzaken veel ongelukken. Systemen in de auto kunnen waarschuwen, maar dan moet een model uit één camerabeeld herkennen of iemand veilig rijdt, afgeleid is, drinkt, slaperig is of gaapt." src="/assets/img/projects/deeplearning_voorbeeldbeelden.png" alt="Raster met voorbeeldbeelden van bestuurders, elk met hun label" photo=true %}

{% include slide.html kicker="Data" title="Zes klassen, ongelijk verdeeld" text="Grijswaardenbeelden van 72 × 128 pixels uit de Kaggle-dataset *Driver Inattention Detection*. Drinken en gapen komen veel minder voor dan veilig rijden." src="/assets/img/projects/deeplearning_klassenverdeling.png" alt="Staafdiagram van het aantal beelden per klasse" %}

{% include models.html kicker="Modellen" title="Zelf bouwen of hergebruiken?" text="Een convolutioneel neuraal netwerk (CNN) leert zelf patronen in beelden herkennen, van randen tot houdingen. We vergeleken een eigen CNN met een voorgetraind netwerk." %}

{% include slide.html kicker="Methode" title="Stap voor stap van 79% naar 95%" text="Elke wijziging is apart getest op een validatieset; alleen wat hielp bleef. De testset is pas aan het eind gebruikt." src="/assets/img/projects/deeplearning_methode.svg" alt="Methodeschema in zes stappen: data, baseline, voorbewerking, tunen, architectuur en evaluatie" full=true %}

{% include slide.html kicker="Resultaten" title="Het eigen CNN wint ruim" text="95% nauwkeurigheid op de testset, tegen 79% voor de baseline en 84% voor DenseNet121. De gemiddelde recall steeg van 0,65 naar 0,92." src="/assets/img/projects/deeplearning_nauwkeurigheid_vergelijking.png" alt="Staafdiagram van de testnauwkeurigheid: baseline 79%, DenseNet121 84%, eigen CNN 95%" %}

{% include slide.html kicker="Resultaten" title="Leert zonder te overfitten" text="Training en validatie blijven dicht bij elkaar. Per klasse ligt de AUC tussen 0,97 en 1,00." src="/assets/img/projects/deeplearning_leercurve_beste_model.png" alt="Lijngrafiek van training- en validatienauwkeurigheid per epoch" src2="/assets/img/projects/deeplearning_roc_beste_model.png" alt2="ROC-curves per klasse met AUC tussen 0,97 en 1,00" full=true %}

{% include slide.html kicker="Evaluatie" title="Sterk, maar niet klaar voor de weg" text="'Afgeleid' en 'veilig rijden' blijven het lastigste paar. Kleurenbeelden en hogere resolutie zouden kunnen helpen. Voor echt gebruik tellen ook bias tussen groepen bestuurders, privacy en beveiliging mee." statement=true %}

<div class="role" markdown="1">
## Mijn rol
Ik bouwde het beste model: de tweede Optuna-ronde, de keuze voor dropout en de architectuur met verdubbelende filters. Ook bereidde ik de beelden voor en deed ik de DenseNet121-experimenten.
</div>
