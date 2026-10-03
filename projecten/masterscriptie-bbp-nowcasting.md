---
layout: project
lang: nl
ref: thesis
project: thesis
section: master
title: "Masterscriptie: economische groei in real time voorspellen met deep learning"
lead: Kunnen neurale netwerken die maand- en kwartaaldata direct combineren de economie beter 'nowcasten' dan de modellen van centrale banken?
description: Drie eigen LSTM- en GRU-architecturen voor het real-time voorspellen van bbp-groei, getoetst tegen Dynamic Factor Models en ARMA.
image: /assets/img/projects/scriptie_rmse_vergelijking.png
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

## De vraag

Officiële cijfers over het bbp verschijnen maar eens per kwartaal en met flinke vertraging, terwijl beleidsmakers en markten nu al willen weten hoe de economie ervoor staat. Kunnen deep-learningmodellen die maand- en kwartaaldata direct combineren een betere real-time schatting (nowcast) geven?

## De data

De FRED-MD- en FRED-QD-datasets van de Federal Reserve Bank of St. Louis: honderden maandelijkse en driemaandelijkse economische indicatoren voor de Verenigde Staten.

## Aanpak

Ik ontwierp drie neurale-netwerkarchitecturen, gebouwd op LSTM en GRU, die gegevens met verschillende frequenties direct verwerken, zonder ze eerst te middelen of ontbrekende waarden in te vullen. Die heb ik getoetst tegen de modellen die centrale banken hiervoor gebruiken (Dynamic Factor Models en ARMA) en tegen netwerken die alleen kwartaaldata zien.

{% include figure.html src="/assets/img/projects/scriptie_methode_stroomschema.png" alt="Stroomschema van de onderzoeksopzet" caption="Opzet van het onderzoek: de modellen worden jaar voor jaar opnieuw getraind op alle data tot dan toe en getest op het jaar erna, tot en met 2024. Daarna volgt de evaluatie over de hele periode, 2000–2019 en de recessies." narrow=true %}

## Resultaten

{% include figure.html src="/assets/img/projects/scriptie_rmse_vergelijking.png" alt="Staafdiagram: de eigen modellen Repeat-LSTM en Alternate-GRU hebben een lagere RMSE dan Quarterly-GRU, het Dynamic Factor Model en ARMA" caption="Fout (RMSE) van de nowcasts voor de VS, 2000–2019. Lager is beter; de blauwe balken zijn mijn eigen architecturen." %}

- **In de periode 2000–2019 verslaan mijn architecturen alle benchmarks.** De beste zit ongeveer 11% onder de fout van het Dynamic Factor Model en 23% onder ARMA.
- Inclusief de COVID-jaren (2000–2024) heeft Alternate-GRU nog steeds de laagste fout van alle modellen.
- Niet elke variant wordt beter naarmate er in het kwartaal meer maanddata binnenkomt: er blijkt een afweging tussen goede voorspellingen aan het begin en aan het eind van een kwartaal.
- In crisisperiodes zijn de modellen niet significant beter dan het Dynamic Factor Model. Dat spreekt eerder onderzoek tegen, dat juist stelde dat niet-lineaire methodes in zulke periodes uitblinken.

{% include figure.html src="/assets/img/projects/scriptie_voorspelling_vs_werkelijk.png" alt="Lijngrafiek van voorspelde en werkelijke bbp-groei 2000–2019 voor het Dynamic Factor Model en Alternate-GRU" caption="Voorspelde en werkelijke bbp-groei, 2000–2019, met de recessies gemarkeerd." wide=true %}

<div class="role" markdown="1">
## Wat ik ervan leerde
Een complexer model is niet automatisch beter. In rustige periodes wonnen mijn netwerken duidelijk, maar juist in crises, waar je het meest aan een goede voorspelling hebt, was het verschil met het klassieke model niet significant. Dat eerlijk laten zien vond ik net zo belangrijk als de winst zelf.
</div>
