---
layout: project
lang: nl
ref: thesis
project: thesis
section: master
title: "Masterscriptie: economische groei in real time voorspellen met deep learning"
lead: "Kan een neuraal netwerk dat maand- en kwartaaldata direct combineert de economie beter 'nowcasten' dan centrale banken?"
description: Drie eigen LSTM- en GRU-architecturen voor het real-time voorspellen van bbp-groei, getoetst tegen Dynamic Factor Models en ARMA.
image: /assets/img/projects/scriptie_rmse_vergelijking.png
abstract: "Het bbp verschijnt per kwartaal en met vertraging, maandcijfers komen veel sneller. Ik ontwierp drie neurale netwerken die beide direct combineren. Van 2000 tot 2019 is hun voorspelfout 11% lager dan die van het model van centrale banken."
course: MSc Data Science and Society, Tilburg University
team: Individueel onderzoek
code: https://github.com/GKruidenier/GDP-nowcasting-thesis
tools: [Python, PyTorch, LSTM, GRU, statsmodels, Dynamic Factor Models, ARMA]
stats:
  - value: "−11%"
    label: lagere fout dan het Dynamic Factor Model (2000–2019)
  - value: "−23%"
    label: lagere fout dan ARMA
  - value: "3"
    label: eigen netwerkarchitecturen ontworpen
models:
  - name: "ARMA"
    tag: "benchmark"
    text: "Voorspelt het bbp alleen uit zijn eigen verleden."
  - name: "Dynamic Factor Model"
    tag: "benchmark"
    text: "De standaard van centrale banken: vat alle indicatoren samen in een paar factoren."
  - name: "Quarterly-RNN"
    tag: "vergelijking"
    text: "Hetzelfde soort netwerk, maar alleen met kwartaalgemiddelden."
  - name: "Repeat-RNN"
    tag: "eigen ontwerp"
    own: true
    text: "Leest elke maand en herhaalt het laatste kwartaalcijfer."
  - name: "Multilayer-RNN"
    tag: "eigen ontwerp"
    own: true
    text: "Een kwartaallaag met daarboven een maandlaag."
  - name: "Alternate-RNN"
    tag: "eigen ontwerp"
    own: true
    text: "Maand- en kwartaalnetwerk wisselen af en delen hun geheugen."
sample:
  caption: "Zo ziet de data eruit"
  columns: ["Maand", "Industrie", "Werkloosheid", "Bbp-groei"]
  rows:
    - ["jan 2024", "101,5", "3,7%", "–"]
    - ["feb 2024", "102,7", "3,9%", "–"]
    - ["mrt 2024", "102,5", "3,9%", "+0,4%"]
    - ["apr 2024", "102,4", "3,9%", "?"]
  note: "Twee van de 238 indicatoren. Het bbp komt eens per kwartaal; het vraagteken is wat het model schat."
---

{% include slide.html kicker="Probleem" title="Hoe gaat het nú met de economie?" text="Het bbp-cijfer komt pas weken na afloop van een kwartaal. Kan een model met de maandcijfers die al binnen zijn de groei van dit kwartaal schatten?" src="/assets/img/projects/scriptie_concept.svg" alt="Schets: maand- en kwartaaldata gaan samen een netwerk in dat de bbp-groei van het lopende kwartaal schat" full=true %}

{% include data.html kicker="Data" title="Maand- en kwartaalcijfers door elkaar" text="121 maand- en 117 kwartaalindicatoren van de Amerikaanse economie, 1960–2024." src="/assets/img/projects/scriptie_bbp_groei_nl.png" alt="Lijngrafiek van de kwartaalgroei van het Amerikaanse bbp 1960–2024, met scherpe dalen in de recessies" %}

{% include models.html kicker="Modellen" title="Twee benchmarks, drie eigen ontwerpen" text="LSTM en GRU zijn netwerken met een geheugen voor tijdreeksen. Ik paste ze aan zodat ze maand- en kwartaaldata tegelijk lezen." %}

{% include slide.html kicker="Methode" title="Van ruwe reeksen tot nowcast" text="Elk jaar opnieuw getraind op alle data tot dan toe en getest op het jaar erna, zoals het in de praktijk zou gaan." src="/assets/img/projects/scriptie_pipeline.svg" alt="Pipeline: maand- en kwartaaldata, stationair maken en featureselectie, een mixed-frequency RNN en als uitkomst de bbp-groei van dit kwartaal" full=true %}

{% include slide.html kicker="Resultaten" title="11% nauwkeuriger dan centrale banken" text="Van 2000 tot 2019 verslaan mijn netwerken (blauw) alle benchmarks, ook ARMA (−23%)." src="/assets/img/projects/scriptie_rmse_vergelijking.png" alt="Staafdiagram: Repeat-LSTM en Alternate-GRU hebben een lagere fout dan Quarterly-GRU, het Dynamic Factor Model en ARMA" %}

{% include slide.html kicker="Evaluatie" title="Complexer is niet altijd beter" text="In crises, juist wanneer het telt, was het verschil met het model van centrale banken niet significant. Dat spreekt eerder onderzoek tegen." statement=true %}
