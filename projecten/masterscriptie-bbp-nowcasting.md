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
abstract_image: /assets/img/projects/scriptie_concept.svg
abstract_alt: "Visuele samenvatting: maand- en kwartaaldata gaan samen een eigen netwerk in dat de bbp-groei van het lopende kwartaal schat"
course: MSc Data Science and Society, Tilburg University
team: Individueel onderzoek
code: https://github.com/GKruidenier/GDP-nowcasting-thesis
tools: [Python, PyTorch, LSTM, GRU, statsmodels, Dynamic Factor Models, ARMA]
stats:
  - value: "−11%"
    label: "minder voorspelfout dan het model van centrale banken (2000–2019)"
  - value: "−23%"
    label: "minder voorspelfout dan een eenvoudige benchmark"
  - value: "3"
    label: "eigen netwerkontwerpen"
models:
  - name: "Eenvoudige benchmark"
    tag: "ARMA"
    text: "Voorspelt het bbp alleen uit zijn eigen verleden."
  - name: "Model van centrale banken"
    tag: "Dynamic Factor Model"
    text: "Vat alle indicatoren samen in een paar onderliggende trends. De standaard om te verslaan."
  - name: "Netwerk met alleen kwartaalcijfers"
    tag: "vergelijking"
    text: "Hetzelfde soort netwerk, maar met maandcijfers eerst gemiddeld per kwartaal."
  - name: "Mijn netwerk 1: herhalen"
    tag: "Repeat-RNN"
    own: true
    text: "Leest elke maand en onthoudt het laatste kwartaalcijfer."
  - name: "Mijn netwerk 2: twee lagen"
    tag: "Multilayer-RNN"
    own: true
    text: "Een laag voor de kwartalen, met daarboven een laag die per maand meeleest."
  - name: "Mijn netwerk 3: afwisselen"
    tag: "Alternate-RNN"
    own: true
    text: "Een maand- en een kwartaalnetwerk wisselen elkaar af en delen hun geheugen."
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

{% include models.html kicker="Modellen" title="Twee benchmarks, drie eigen ontwerpen" text="Mijn netwerken hebben een geheugen voor reeksen in de tijd (LSTM of GRU). Ik paste ze aan zodat ze maand- en kwartaalcijfers tegelijk kunnen lezen." %}

{% include slide.html kicker="Methode" title="Van ruwe cijfers tot schatting" text="Het model ziet nooit cijfers uit de toekomst: elk jaar wordt het opnieuw getraind op alle data tot dan toe en getest op het jaar erna." src="/assets/img/projects/scriptie_pipeline.svg" alt="Pipeline: maand- en kwartaalcijfers, trends eruit halen en de beste cijfers kiezen, een eigen netwerk en als uitkomst de bbp-groei van dit kwartaal" full=true %}

{% include slide.html kicker="Resultaten" title="11% nauwkeuriger dan centrale banken" text="Van 2000 tot 2019 maken mijn netwerken (blauw) een kleinere fout dan alle benchmarks: 11% minder dan het model van centrale banken en 23% minder dan de eenvoudige benchmark." src="/assets/img/projects/scriptie_resultaat.svg" alt="Staafdiagram: met het model van centrale banken op 100 scoren mijn netwerken 89 en 90, de eenvoudige benchmark 115" full=true %}

{% include slide.html kicker="Evaluatie" title="Complexer is niet altijd beter" text="In crises, juist wanneer het telt, was het verschil met het model van centrale banken niet significant. Dat spreekt eerder onderzoek tegen." statement=true %}
