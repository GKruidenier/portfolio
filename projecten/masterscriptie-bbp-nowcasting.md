---
layout: project
lang: nl
ref: thesis
project: thesis
section: master
title: "Masterscriptie: economische groei in real time voorspellen met deep learning"
lead: "Kan een neuraal netwerk dat maand- en kwartaaldata direct combineert de economie beter 'nowcasten' dan het klassieke nowcastmodel?"
description: Drie eigen LSTM- en GRU-architecturen voor het real-time voorspellen van bbp-groei, getoetst tegen een Dynamic Factor Model en ARMA.
image: /assets/img/projects/scriptie_rmse_vergelijking.png
abstract: "Het bbp verschijnt per kwartaal en met vertraging, maandcijfers komen veel sneller. Ik ontwierp drie neurale netwerken die beide direct combineren. Van 2000 tot 2019 is hun voorspelfout 11% lager dan die van een Dynamic Factor Model: het type model dat centrale banken gebruiken, door mij in een eenvoudige vorm toegepast op dezelfde data."
abstract_image: /assets/img/projects/scriptie_concept.svg
abstract_alt: "Visuele samenvatting: maand- en kwartaaldata gaan samen een eigen netwerk in dat de bbp-groei van het lopende kwartaal schat"
course: MSc Data Science and Society, Tilburg University
team: Individueel onderzoek
code: https://github.com/GKruidenier/GDP-nowcasting-thesis
tools: [Python, PyTorch, LSTM, GRU, statsmodels, Dynamic Factor Models, ARMA]
stats:
  - value: "−11%"
    label: "minder voorspelfout dan een Dynamic Factor Model op dezelfde data (2000–2019)"
  - value: "−23%"
    label: "minder voorspelfout dan een eenvoudige benchmark"
  - value: "3"
    label: "eigen netwerkontwerpen"
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

{% include slide.html kicker="Probleem" title="Hoe gaat het nú met de economie?" text="Het bbp-cijfer komt pas weken na afloop van een kwartaal. Kan een model met de maandcijfers die al binnen zijn de groei van dit kwartaal schatten? Dat heet nowcasting." src="/assets/img/projects/scriptie_probleem.svg" alt="Tijdlijn: maandcijfers komen elke maand binnen, maar het bbp van het eerste kwartaal is pas weken na afloop van het kwartaal bekend" full=true %}

{% include data.html kicker="Data" title="Maand- en kwartaalcijfers door elkaar" text="121 maand- en 117 kwartaalindicatoren van de Amerikaanse economie, 1960–2024." src="/assets/img/projects/scriptie_bbp_groei_nl.png" alt="Lijngrafiek van de kwartaalgroei van het Amerikaanse bbp 1960–2024, met scherpe dalen in de recessies" %}

{% include slide.html kicker="Modellen" title="Drie manieren om maand en kwartaal te combineren" text="Alle modellen krijgen dezelfde cijfers. Mijn netwerken (LSTM en GRU) hebben een geheugen en zetten stap voor stap door de tijd. Het verschil zit in hoe maand- en kwartaalcijfers samenkomen." src="/assets/img/projects/scriptie_modellen.svg" alt="Zes modellen. Benchmarks: ARMA gebruikt alleen het eigen verleden van het bbp, een eenvoudige versie van het Dynamic Factor Model van centrale banken vat de cijfers samen in een paar trends, en een netwerk op kwartaalcijfers middelt de maandcijfers eerst. Mijn ontwerpen: herhalen (elke maand een stap, het kwartaalcijfer leest mee), twee lagen (een kwartaallaag voedt een maandlaag) en afwisselen (kwartaal- en maandnetwerk delen om de beurt één geheugen)" full=true %}

{% include slide.html kicker="Methode" title="Van ruwe cijfers tot schatting" text="Het model ziet nooit cijfers uit de toekomst: elk jaar wordt het opnieuw getraind op alle data tot dan toe en getest op het jaar erna." src="/assets/img/projects/scriptie_pipeline.svg" alt="Pipeline: maand- en kwartaalcijfers, trends eruit halen en de beste cijfers kiezen, een eigen netwerk en als uitkomst de bbp-groei van dit kwartaal" full=true %}

{% include slide.html kicker="Resultaten" title="11% kleinere fout dan het klassieke model" text="Van 2000 tot 2019 maken mijn netwerken (blauw) een kleinere fout dan alle benchmarks: 11% minder dan het Dynamic Factor Model en 23% minder dan de eenvoudige benchmark." src="/assets/img/projects/scriptie_resultaat.svg" alt="Staafdiagram: met het Dynamic Factor Model op 100 scoren mijn netwerken 89 en 90, de eenvoudige benchmark 115" full=true %}

{% include slide.html kicker="Evaluatie" title="Beter dan het model, niet beter dan centrale banken" text="Mijn Dynamic Factor Model is een eenvoudige versie op dezelfde data als mijn netwerken, met 9 tot 20 indicatoren. Centrale banken gebruiken een veel uitgebreidere versie: meer databronnen, groepen van indicatoren en een update bij elke nieuwe publicatie. Mijn resultaat zegt dus dat de netwerken het klassieke model verslaan, niet de nowcasts van centrale banken. Ook was het verschil in crises, juist wanneer het telt, niet significant." statement=true %}
