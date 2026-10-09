---
layout: project
lang: en
ref: thesis
project: thesis
section: master
title: "Master's thesis: nowcasting economic growth with deep learning"
lead: "Can a neural network that combines monthly and quarterly data directly 'nowcast' the economy better than the classic nowcasting model?"
description: Three custom LSTM and GRU architectures for nowcasting GDP growth in real time, tested against a Dynamic Factor Model and ARMA.
image: /assets/img/projects/scriptie_rmse_vergelijking_en.png
abstract: "GDP is published quarterly and with a delay, while monthly figures arrive much sooner. I designed three neural networks that combine both directly. From 2000 to 2019 their forecast error is 11% lower than that of a Dynamic Factor Model: the type of model central banks use, which I applied in a simple form to the same data."
abstract_image: /assets/img/projects/scriptie_concept_en.svg
abstract_alt: "Visual summary: monthly and quarterly data feed a custom network that estimates GDP growth for the current quarter"
course: MSc Data Science and Society, Tilburg University
team: Individual research
code: https://github.com/GKruidenier/GDP-nowcasting-thesis
tools: [Python, PyTorch, LSTM, GRU, statsmodels, Dynamic Factor Models, ARMA]
stats:
  - value: "−11%"
    label: "less forecast error than a Dynamic Factor Model on the same data (2000–2019)"
  - value: "−23%"
    label: "less forecast error than a simple benchmark"
  - value: "3"
    label: "own network designs"
sample:
  caption: "What the data looks like"
  columns: ["Month", "Industry", "Unemployment", "GDP growth"]
  rows:
    - ["Jan 2024", "101.5", "3.7%", "–"]
    - ["Feb 2024", "102.7", "3.9%", "–"]
    - ["Mar 2024", "102.5", "3.9%", "+0.4%"]
    - ["Apr 2024", "102.4", "3.9%", "?"]
  note: "Two of the 238 indicators. GDP arrives once a quarter; the question mark is what the model estimates."
---

{% include slide.html kicker="Problem" title="How is the economy doing right now?" text="The GDP figure arrives weeks after a quarter ends. Can a model use the monthly figures already in to estimate this quarter's growth? That is called nowcasting." src="/assets/img/projects/scriptie_probleem_en.svg" alt="Timeline: monthly figures arrive every month, but first-quarter GDP is only known weeks after the quarter ends" full=true %}

{% include data.html kicker="Data" title="Monthly and quarterly figures mixed" text="121 monthly and 117 quarterly indicators of the US economy, 1960–2024." src="/assets/img/projects/scriptie_bbp_groei_en.png" alt="Line chart of quarterly US GDP growth 1960–2024, with sharp drops in recessions" %}

{% include slide.html kicker="Models" title="Three ways to combine month and quarter" text="All models get the same figures. My networks (LSTM and GRU) have a memory and step through time. The difference is how monthly and quarterly figures come together." src="/assets/img/projects/scriptie_modellen_en.svg" alt="Six models. Benchmarks: ARMA uses only the past of GDP, a simple version of the central banks' Dynamic Factor Model sums up the figures in a few trends, and a network on quarterly data averages the monthly figures first. My designs: repeat (one step per month, the quarterly figure is read along), two layers (a quarterly layer feeds a monthly layer) and alternate (quarterly and monthly network take turns with one shared memory)" full=true %}

{% include slide.html kicker="Method" title="From raw figures to estimate" text="The model never sees figures from the future: every year it is retrained on all data so far and tested on the following year." src="/assets/img/projects/scriptie_pipeline_en.svg" alt="Pipeline: monthly and quarterly figures, removing trends and picking the best figures, an own network and as output this quarter's GDP growth" full=true %}

{% include slide.html kicker="Results" title="11% smaller error than the classic model" text="From 2000 to 2019 my networks (blue) make a smaller error than all benchmarks: 11% less than the Dynamic Factor Model and 23% less than the simple benchmark." src="/assets/img/projects/scriptie_resultaat_en.svg" alt="Bar chart: with the Dynamic Factor Model at 100, my networks score 89 and 90, the simple benchmark 115" full=true %}

{% include slide.html kicker="Evaluation" title="Better than the model, not better than central banks" text="My Dynamic Factor Model is a simple version on the same data as my networks, with 9 to 20 indicators. Central banks run a far more extensive version: more data sources, groups of indicators and an update with every new release. So my result says the networks beat the classic model, not the nowcasts of central banks. Also, in crises, exactly when it matters, the difference was not significant." statement=true %}
