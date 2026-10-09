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
abstract: "Het bbp verschijnt per kwartaal en met vertraging, maandcijfers komen veel sneller. Ik ontwierp drie neurale netwerken die beide direct combineren, elk in een LSTM- en een GRU-versie. Van 2000 tot 2019 is de voorspelfout van vijf van die zes ongeveer 10% lager dan die van een Dynamic Factor Model: het type model dat centrale banken gebruiken, door mij in een eenvoudige vorm toegepast op dezelfde data."
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
---

{% include slide.html kicker="Probleem" title="Hoe gaat het nú met de economie?" text="Het bbp-cijfer komt pas weken na afloop van een kwartaal. Kan een model met de maandcijfers die al binnen zijn de groei van dit kwartaal schatten? Dat heet nowcasting." src="/assets/img/projects/scriptie_probleem.svg" alt="Tijdlijn: maandcijfers komen elke maand binnen, maar het bbp van het eerste kwartaal is pas weken na afloop van het kwartaal bekend" full=true %}

{% include slide.html kicker="Aanleiding" title="Bestaande modellen, twee nieuwe vragen" text="Bijna elke grote centrale bank heeft een nowcastmodel, vaak een Dynamic Factor Model. Machine learning wordt vooral nog onderzocht en soms naast het Dynamic Factor Model gebruikt, zoals bij het IMF. Voor deep learning bestaan voor het bbp nog maar een handvol studies. Bovendien middelen die studies de maandcijfers meestal eerst tot kwartalen of vullen ze kunstmatig aan, waardoor informatie verloren gaat. Om de maandcijfers wél mee te nemen, moest ik de architectuur van de netwerken aanpassen." src="/assets/img/projects/scriptie_aanleiding.svg" alt="Van klassieke modellen (Dynamic Factor Model, bij bijna elke centrale bank) via machine learning (maandcijfers eerst gemiddeld) naar deep learning dat maand- en kwartaalcijfers direct leest. Onderzoeksvraag 1: kan deep learning het bbp nowcasten en hoe doet het dat ten opzichte van de klassieke modellen? Onderzoeksvraag 2: wordt de schatting van het huidige kwartaal beter als het model ook de maandcijfers meeleest?" full=true %}

{% include slide.html kicker="Modellen" title="Drie manieren om maand en kwartaal te combineren" text="Op ARMA na werken alle modellen met een selectie uit dezelfde 238 maand- en kwartaalindicatoren van de Amerikaanse economie (1960–2024). Mijn netwerken (LSTM en GRU) hebben een geheugen en zetten stap voor stap door de tijd. Het verschil zit in hoe maand- en kwartaalcijfers samenkomen." src="/assets/img/projects/scriptie_modellen.svg" alt="Zes modellen. Benchmarks: het klassieke tijdreeksmodel ARMA gebruikt alleen het eigen verleden van het bbp, een eenvoudige versie van het Dynamic Factor Model van centrale banken vat de cijfers samen in een paar trends, en een netwerk op kwartaalcijfers middelt de maandcijfers eerst. Mijn ontwerpen: herhalen (elke maand een stap, het kwartaalcijfer leest mee), twee lagen (een kwartaallaag voedt een maandlaag) en afwisselen (kwartaal- en maandnetwerk delen om de beurt één geheugen)" full=true %}

{% include slide.html kicker="Resultaat vraag 1" title="Deep learning voorspelt beter dan de klassieke modellen" text="Van 2000 tot 2019 was de voorspelfout van vijf van mijn zes netwerken die maand- en kwartaalcijfers combineren ongeveer 10% kleiner dan die van het Dynamic Factor Model, en ruim 20% kleiner dan die van het tijdreeksmodel ARMA." src="/assets/img/projects/scriptie_echt_vs_voorspeld.svg" alt="Lijngrafiek van de echte en geschatte bbp-groei per kwartaal, 2000–2019. Beide modellen volgen de grote bewegingen; deep learning zit gemiddeld het dichtst bij de echte groei, maar dempt pieken en dalen wat af. Gemiddelde afwijking: ARMA 0,58, Dynamic Factor Model 0,50, deep learning 0,45 procentpunt." full=true %}

{% include slide.html kicker="Resultaat vraag 2" title="Maandcijfers meelezen maakt de schatting beter" text="Een vergelijkbaar GRU-netwerk maakt een 4% kleinere fout als het naast de kwartaalcijfers ook de maandcijfers leest. Zo schat het de diepe val eind 2008 veel beter in." src="/assets/img/projects/scriptie_echt_vs_voorspeld_vraag2.svg" alt="Lijngrafiek van de echte bbp-groei en twee deep-learningnetwerken, 2000–2019. Het netwerk met maand- en kwartaalcijfers schat de diepe val eind 2008 veel beter in dan het netwerk op alleen kwartaalcijfers. Gemiddelde afwijking: 0,47 tegen 0,45 procentpunt." full=true %}

{% include slide.html kicker="Evaluatie" title="Kanttekeningen en vervolg" points="**Crises:** daar was het Dynamic Factor Model ongeveer even goed als mijn beste netwerk, en in 2008 zelfs beter. Eerder onderzoek vond juist dat machine learning vooral in crises wint. | **Corona:** met de jaren tot en met 2024 erbij verslaat alleen het afwisselende GRU-netwerk het Dynamic Factor Model nog. | **Nieuwe maandcijfers:** bij de meeste modellen werd de schatting na het eerste maandcijfer eerst slechter. Alleen dat GRU-netwerk werd elke maand beter. | **Eenvoudig vergelijkingsmodel:** mijn Dynamic Factor Model is een eenvoudige versie op dezelfde data. Over de veel uitgebreidere nowcasts van centrale banken zegt dit dus niets. | **Vervolg:** een model dat op elk moment een nowcast maakt, met alles wat er dan bekend is, zoals dagelijkse cijfers van de financiële markten. Testen kan tegen het kwartaalcijfer, maar vraagt de data zoals die op elk moment bekend was, inclusief latere correcties." statement=true %}
