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
abstract: "Het bbp verschijnt per kwartaal en met vertraging, maanddata komt veel sneller binnen. Ik ontwierp drie LSTM- en GRU-architecturen die beide frequenties direct verwerken en toetste ze jaar voor jaar tegen de modellen van centrale banken. Tussen 2000 en 2019 zitten ze 11% onder de fout van het Dynamic Factor Model; in crises is het verschil niet significant."
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
---

{% include slide.html title="Het idee" text="Eén netwerk leest maand- en kwartaaldata tegelijk en schat de groei van dit kwartaal, nog voordat het officiële cijfer er is." src="/assets/img/projects/scriptie_concept.svg" alt="Schets: maanddata en kwartaaldata gaan samen een terugkoppelend netwerk in, dat het bbp van het lopende kwartaal schat" full=true %}

{% include slide.html title="De opzet" text="Elk jaar opnieuw getraind op alle data sinds 1960 en getest op het jaar erna, tot en met 2024." src="/assets/img/projects/scriptie_opzet.svg" alt="Tijdlijn: per ronde groeit de trainingsperiode vanaf 1960 met een jaar en wordt het volgende jaar getest; evaluatie over 2000–2024, 2000–2019 en de recessies" full=true %}

{% include slide.html title="Beter dan de benchmark" text="Van 2000 tot 2019 verslaan mijn architecturen (blauw) alle benchmarks: **11% minder fout** dan het Dynamic Factor Model, 23% minder dan ARMA." src="/assets/img/projects/scriptie_rmse_vergelijking.png" alt="Staafdiagram: Repeat-LSTM en Alternate-GRU hebben een lagere RMSE dan Quarterly-GRU, het Dynamic Factor Model en ARMA" %}

{% include slide.html title="Voorspeld tegen werkelijk" text="Alternate-GRU volgt de groei nauw. Ook inclusief de COVID-jaren heeft het de laagste fout van alle modellen." src="/assets/img/projects/scriptie_voorspelling_vs_werkelijk.png" alt="Lijngrafiek van voorspelde en werkelijke bbp-groei 2000–2019 met de recessies gemarkeerd" full=true %}

{% include slide.html title="Complexer is niet altijd beter" text="Juist in crises, waar je een goede voorspelling het hardst nodig hebt, was het verschil met het klassieke model niet significant. Dat eerlijk laten zien hoort bij het resultaat." statement=true %}
