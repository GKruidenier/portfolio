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
abstract: "Het bbp verschijnt per kwartaal en met vertraging, maandcijfers komen veel sneller. Ik ontwierp drie neurale netwerken die beide direct combineren. Van 2000 tot 2019 is hun voorspelfout ongeveer 10% lager dan die van een Dynamic Factor Model: het type model dat centrale banken gebruiken, door mij in een eenvoudige vorm toegepast op dezelfde data."
abstract_image: /assets/img/projects/scriptie_concept.svg
abstract_alt: "Visuele samenvatting: maand- en kwartaaldata gaan samen een eigen netwerk in dat de bbp-groei van het lopende kwartaal schat"
course: MSc Data Science and Society, Tilburg University
team: Individueel onderzoek
code: https://github.com/GKruidenier/GDP-nowcasting-thesis
tools: [Python, PyTorch, LSTM, GRU, statsmodels, Dynamic Factor Models, ARMA]
stats:
  - value: "−10%"
    label: "minder voorspelfout dan een Dynamic Factor Model op dezelfde data (2000–2019)"
  - value: "−4%"
    label: "minder voorspelfout als het netwerk ook de maandcijfers leest"
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

{% include slide.html kicker="Aanleiding" title="Bestaande modellen, twee nieuwe vragen" text="Bijna elke centrale bank heeft een nowcastmodel, meestal een Dynamic Factor Model. Machine learning is alleen in wetenschappelijke studies getest, en deep learning voor het bbp nog maar in enkele. Bovendien middelen die studies de maandcijfers eerst tot kwartalen, waardoor informatie verloren gaat. Om de maandcijfers wél mee te nemen, moest ik de architectuur van de netwerken aanpassen." src="/assets/img/projects/scriptie_aanleiding.svg" alt="Van klassieke modellen (Dynamic Factor Model, bij bijna elke centrale bank) via machine learning (maandcijfers eerst gemiddeld) naar deep learning dat maand- en kwartaalcijfers direct leest. Onderzoeksvraag 1: kan deep learning het bbp nowcasten en hoe doet het dat ten opzichte van de klassieke modellen? Onderzoeksvraag 2: wordt de schatting van het huidige kwartaal beter als het model ook de maandcijfers meeleest?" full=true %}

{% include data.html kicker="Data" title="Maand- en kwartaalcijfers door elkaar" text="121 maand- en 117 kwartaalindicatoren van de Amerikaanse economie, 1960–2024." src="/assets/img/projects/scriptie_bbp_groei_nl.png" alt="Lijngrafiek van de kwartaalgroei van het Amerikaanse bbp 1960–2024, met scherpe dalen in de recessies" %}

{% include slide.html kicker="Modellen" title="Drie manieren om maand en kwartaal te combineren" text="Alle modellen krijgen dezelfde cijfers. Mijn netwerken (LSTM en GRU) hebben een geheugen en zetten stap voor stap door de tijd. Het verschil zit in hoe maand- en kwartaalcijfers samenkomen." src="/assets/img/projects/scriptie_modellen.svg" alt="Zes modellen. Benchmarks: het klassieke tijdreeksmodel ARMA gebruikt alleen het eigen verleden van het bbp, een eenvoudige versie van het Dynamic Factor Model van centrale banken vat de cijfers samen in een paar trends, en een netwerk op kwartaalcijfers middelt de maandcijfers eerst. Mijn ontwerpen: herhalen (elke maand een stap, het kwartaalcijfer leest mee), twee lagen (een kwartaallaag voedt een maandlaag) en afwisselen (kwartaal- en maandnetwerk delen om de beurt één geheugen)" full=true %}

{% include slide.html kicker="Resultaat vraag 1" title="Deep learning voorspelt beter dan de klassieke modellen" text="Van 2000 tot 2019 was de voorspelfout van mijn deep-learningmodellen die maand- en kwartaalcijfers combineren ongeveer 10% kleiner dan die van het Dynamic Factor Model, en ruim 20% kleiner dan die van het tijdreeksmodel ARMA." src="/assets/img/projects/scriptie_echt_vs_voorspeld.svg" alt="Lijngrafiek van de echte en geschatte bbp-groei per kwartaal, 2000–2019. De lijn van deep learning volgt de echte groei het dichtst, ook in de recessie van 2008–2009. Gemiddelde afwijking: ARMA 0,58, Dynamic Factor Model 0,50, deep learning 0,45 procentpunt." full=true %}

{% include slide.html kicker="Resultaat vraag 2" title="Maandcijfers meelezen maakt de schatting beter" text="Hetzelfde type netwerk maakt een 4% kleinere fout als het naast de kwartaalcijfers ook de maandcijfers leest." src="/assets/img/projects/scriptie_resultaat_vraag2.svg" alt="Staafdiagram van hoe ver de schatting gemiddeld naast de echte bbp-groei zit: deep learning op alleen kwartaalcijfers zit er gemiddeld 0,47 procentpunt naast, deep learning met maand- en kwartaalcijfers 0,45. Dat is 4% minder." full=true %}

{% include slide.html kicker="Evaluatie" title="Wat beter kan, en wat het niet zegt" text="Verrassend: bij de meeste modellen werd de schatting na het eerste nieuwe maandcijfer eerst slechter. Alleen het afwisselende GRU-netwerk werd elke maand beter. In crises waren mijn netwerken niet significant beter dan het Dynamic Factor Model, anders dan eerder onderzoek vond. En mijn Dynamic Factor Model is een eenvoudige versie op dezelfde data. Centrale banken gebruiken een veel uitgebreidere versie, dus over hun nowcasts zegt dit niets." statement=true %}
