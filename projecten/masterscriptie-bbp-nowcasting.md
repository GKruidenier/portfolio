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
models:
  - name: "ARMA"
    tag: "benchmark"
    text: "Voorspelt de groei alleen uit het eigen verleden van het bbp. De makkelijk te verslaan ondergrens."
  - name: "Dynamic Factor Model"
    tag: "benchmark"
    text: "Vat honderden indicatoren samen in een paar onderliggende factoren. De standaard bij centrale banken en moeilijk te verslaan."
  - name: "Quarterly-RNN"
    tag: "vergelijking"
    text: "Een LSTM/GRU-netwerk dat maanddata eerst middelt tot kwartalen. Laat zien wat de mixed-frequency aanpak toevoegt."
  - name: "Repeat-RNN"
    tag: "eigen ontwerp"
    own: true
    text: "Draait per maand en herhaalt de laatst bekende kwartaalwaarde tot er een nieuwe is."
  - name: "Multilayer-RNN"
    tag: "eigen ontwerp"
    own: true
    text: "Een onderste laag leest de kwartalen, een laag daarboven leest elke maand mee."
  - name: "Alternate-RNN"
    tag: "eigen ontwerp"
    own: true
    text: "Een kwartaal- en een maandnetwerk wisselen elkaar af en delen hetzelfde geheugen."
---

{% include slide.html kicker="Probleem" title="Het bbp komt altijd te laat" text="Het officiële bbp-cijfer verschijnt pas weken na afloop van een kwartaal, terwijl beleidsmakers nu moeten beslissen. Maandcijfers over banen, productie en rente komen veel sneller. Kan een neuraal netwerk die maandcijfers direct gebruiken om de groei van dít kwartaal te schatten? Dat heet nowcasting." src="/assets/img/projects/scriptie_concept.svg" alt="Schets: maanddata en kwartaaldata gaan samen een terugkoppelend netwerk in, dat het bbp van het lopende kwartaal schat" full=true %}

{% include slide.html kicker="Data" title="Zestig jaar Amerikaanse economie" text="121 maandelijkse en 117 driemaandelijkse indicatoren uit FRED-MD en FRED-QD, van 1960 tot en met 2024. De groei is meestal rustig, met scherpe dalen in recessies. COVID (2020) is de grootste schok in de hele reeks." src="/assets/img/projects/scriptie_bbp_groei.png" alt="Lijngrafiek van de kwartaalgroei van het Amerikaanse bbp 1960–2024 met recessies grijs gemarkeerd" full=true %}

{% include slide.html kicker="Data" title="Hoe later in het kwartaal, hoe meer signaal" text="Maandcijfers uit later in het kwartaal hangen duidelijk sterker samen met het bbp. Precies die extra informatie wil een nowcastmodel benutten zodra ze binnenkomt." src="/assets/img/projects/scriptie_correlatie_binnen_kwartaal.png" alt="Lijngrafiek: de gemiddelde correlatie met het bbp is hoger voor maanddata uit de tweede en derde maand van het kwartaal" %}

{% include models.html kicker="Modellen" title="Twee benchmarks, drie eigen ontwerpen" text="LSTM en GRU zijn neurale netwerken met een geheugen, gemaakt voor reeksen in de tijd. Ze verwachten echter elke stap dezelfde soort data. Daarom ontwierp ik drie varianten die maand- en kwartaaldata naast elkaar kunnen lezen, elk getest met LSTM én met GRU." %}

{% include slide.html kicker="Methode" title="Van ruwe reeksen tot eerlijke toets" text="Alle stappen van data tot evaluatie. De modellen zien nooit data uit de toekomst: per jaar wordt opnieuw getraind en alleen het jaar erna voorspeld." src="/assets/img/projects/scriptie_methode.svg" alt="Methodeschema in zes stappen: data, voorbewerken, featureselectie met LARS, modellen, recursief testen en evaluatie" full=true %}

{% include slide.html kicker="Methode" title="Zoals het in de praktijk zou gaan" text="Elk jaar opnieuw getraind op alle data sinds 1960 en getest op het jaar erna. Elke run vijf keer herhaald met een andere seed, zodat toeval geen rol speelt." src="/assets/img/projects/scriptie_opzet.svg" alt="Tijdlijn: per ronde groeit de trainingsperiode vanaf 1960 met een jaar en wordt het volgende jaar getest" full=true %}

{% include slide.html kicker="Resultaten" title="Beter dan de benchmark" text="Van 2000 tot 2019 verslaan mijn architecturen (blauw) alle benchmarks: **11% minder fout** dan het Dynamic Factor Model en 23% minder dan ARMA." src="/assets/img/projects/scriptie_rmse_vergelijking.png" alt="Staafdiagram: Repeat-LSTM en Alternate-GRU hebben een lagere RMSE dan Quarterly-GRU, het Dynamic Factor Model en ARMA" %}

{% include slide.html kicker="Resultaten" title="Voorspeld tegen werkelijk" text="Alternate-GRU volgt de groei nauw. Ook inclusief de COVID-jaren heeft het de laagste fout van alle modellen." src="/assets/img/projects/scriptie_voorspelling_vs_werkelijk.png" alt="Lijngrafiek van voorspelde en werkelijke bbp-groei 2000–2019 met de recessies gemarkeerd" full=true %}

{% include slide.html kicker="Evaluatie" title="Complexer is niet altijd beter" text="In crises, juist wanneer een goede voorspelling het meest telt, was het verschil met het Dynamic Factor Model niet significant. Dat spreekt eerder onderzoek tegen. Ook bleek er een afweging: sommige varianten zijn sterk aan het begin van een kwartaal, andere aan het eind." statement=true %}
