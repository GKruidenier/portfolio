---
layout: project
lang: en
ref: thesis
project: thesis
section: master
title: "Master's thesis: nowcasting economic growth with deep learning"
lead: "Can a neural network that combines monthly and quarterly data directly 'nowcast' the economy better than central banks?"
description: Three custom LSTM and GRU architectures for nowcasting GDP growth, tested against Dynamic Factor Models and ARMA.
image: /assets/img/projects/scriptie_rmse_vergelijking_en.png
abstract: "GDP is published quarterly and with a delay, while monthly data arrives much sooner. I designed three LSTM and GRU architectures that process both frequencies directly and tested them year by year against the models central banks use. Between 2000 and 2019 they are 11% below the error of the Dynamic Factor Model; in crises the difference is not significant."
course: MSc Data Science and Society, Tilburg University
team: Individual research
code: https://github.com/GKruidenier/GDP-nowcasting-thesis
tools: [Python, PyTorch, LSTM, GRU, statsmodels, Dynamic Factor Models, ARMA]
stats:
  - value: "−11%"
    label: lower error than the Dynamic Factor Model (2000–2019)
  - value: "−23%"
    label: lower error than ARMA
  - value: "3"
    label: custom network architectures designed
---

{% include slide.html title="The idea" text="One network reads monthly and quarterly data at once and estimates this quarter's growth before the official figure is out." src="/assets/img/projects/scriptie_concept_en.svg" alt="Sketch: monthly and quarterly data feed into a recurrent network that estimates GDP for the current quarter" full=true %}

{% include slide.html title="The setup" text="Retrained every year on all data since 1960 and tested on the following year, up to and including 2024." src="/assets/img/projects/scriptie_opzet_en.svg" alt="Timeline: each round the training period from 1960 grows by one year and the next year is tested; evaluation over 2000–2024, 2000–2019 and recessions" full=true %}

{% include slide.html title="Beating the benchmark" text="From 2000 to 2019 my architectures (blue) beat every benchmark: **11% lower error** than the Dynamic Factor Model and 23% lower than ARMA." src="/assets/img/projects/scriptie_rmse_vergelijking_en.png" alt="Bar chart: Repeat-LSTM and Alternate-GRU have a lower RMSE than Quarterly-GRU, the Dynamic Factor Model and ARMA" %}

{% include slide.html title="Predicted versus actual" text="Alternate-GRU tracks growth closely. Including the COVID years it still has the lowest error of all models." src="/assets/img/projects/scriptie_voorspelling_vs_werkelijk.png" alt="Line chart of predicted and actual GDP growth 2000–2019 with recessions marked" full=true %}

{% include slide.html title="More complex is not always better" text="In crises, exactly when a good forecast matters most, the difference with the classic model was not significant. Showing that honestly is part of the result." statement=true %}
