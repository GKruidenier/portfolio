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
models:
  - name: "ARMA"
    tag: "benchmark"
    text: "Predicts growth from GDP's own past only. The easy-to-beat lower bound."
  - name: "Dynamic Factor Model"
    tag: "benchmark"
    text: "Summarises hundreds of indicators into a few underlying factors. The central-bank standard and hard to beat."
  - name: "Quarterly-RNN"
    tag: "comparison"
    text: "An LSTM/GRU network that first averages monthly data into quarters. Shows what the mixed-frequency approach adds."
  - name: "Repeat-RNN"
    tag: "own design"
    own: true
    text: "Runs monthly and repeats the last known quarterly value until a new one arrives."
  - name: "Multilayer-RNN"
    tag: "own design"
    own: true
    text: "A bottom layer reads the quarters, a layer on top reads along every month."
  - name: "Alternate-RNN"
    tag: "own design"
    own: true
    text: "A quarterly and a monthly network take turns and share the same memory."
---

{% include slide.html kicker="Problem" title="GDP always arrives late" text="The official GDP figure is published weeks after a quarter ends, while policymakers have to decide now. Monthly data on jobs, production and interest rates arrives much sooner. Can a neural network use those monthly figures directly to estimate growth for this quarter? That is called nowcasting." src="/assets/img/projects/scriptie_concept_en.svg" alt="Sketch: monthly and quarterly data feed into a recurrent network that estimates GDP for the current quarter" full=true %}

{% include slide.html kicker="Data" title="Sixty years of the US economy" text="121 monthly and 117 quarterly indicators from FRED-MD and FRED-QD, from 1960 up to and including 2024. Growth is usually calm, with sharp drops in recessions. COVID (2020) is the largest shock in the whole series." src="/assets/img/projects/scriptie_bbp_groei.png" alt="Line chart of quarterly US GDP growth 1960–2024 with recessions shaded grey" full=true %}

{% include slide.html kicker="Data" title="Later in the quarter, more signal" text="Monthly figures from later in the quarter are clearly more strongly related to GDP. That extra information is exactly what a nowcasting model should use as it comes in." src="/assets/img/projects/scriptie_correlatie_binnen_kwartaal.png" alt="Line chart: average correlation with GDP is higher for monthly data from the second and third month of the quarter" %}

{% include models.html kicker="Models" title="Two benchmarks, three own designs" text="LSTM and GRU are neural networks with a memory, built for sequences over time. But they expect the same kind of data at every step. So I designed three variants that read monthly and quarterly data side by side, each tested with LSTM and with GRU." %}

{% include slide.html kicker="Method" title="From raw series to a fair test" text="Every step from data to evaluation. The models never see future data: they are retrained each year and only predict the following year." src="/assets/img/projects/scriptie_methode_en.svg" alt="Six-step method diagram: data, preprocessing, feature selection with LARS, models, recursive testing and evaluation" full=true %}

{% include slide.html kicker="Method" title="As it would work in practice" text="Retrained every year on all data since 1960 and tested on the following year. Every run repeated with five seeds so that chance plays no role." src="/assets/img/projects/scriptie_opzet_en.svg" alt="Timeline: each round the training period from 1960 grows by one year and the next year is tested" full=true %}

{% include slide.html kicker="Results" title="Beating the benchmark" text="From 2000 to 2019 my architectures (blue) beat every benchmark: **11% lower error** than the Dynamic Factor Model and 23% lower than ARMA." src="/assets/img/projects/scriptie_rmse_vergelijking_en.png" alt="Bar chart: Repeat-LSTM and Alternate-GRU have a lower RMSE than Quarterly-GRU, the Dynamic Factor Model and ARMA" %}

{% include slide.html kicker="Results" title="Predicted versus actual" text="Alternate-GRU tracks growth closely. Including the COVID years it still has the lowest error of all models." src="/assets/img/projects/scriptie_voorspelling_vs_werkelijk.png" alt="Line chart of predicted and actual GDP growth 2000–2019 with recessions marked" full=true %}

{% include slide.html kicker="Evaluation" title="More complex is not always better" text="In crises, exactly when a good forecast matters most, the difference with the Dynamic Factor Model was not significant. That contradicts earlier research. There was also a trade-off: some variants are strong early in a quarter, others at the end." statement=true %}
