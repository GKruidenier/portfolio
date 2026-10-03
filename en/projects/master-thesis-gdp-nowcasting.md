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
abstract: "GDP is published quarterly and with a delay, while monthly figures arrive much sooner. I designed three neural networks that combine both directly. From 2000 to 2019 their forecast error is 11% lower than that of the central-bank model."
abstract_image: /assets/img/projects/scriptie_concept_en.svg
abstract_alt: "Visual summary: monthly and quarterly data feed a custom network that estimates GDP growth for the current quarter"
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
    text: "Predicts GDP from its own past only."
  - name: "Dynamic Factor Model"
    tag: "benchmark"
    text: "The central-bank standard: summarises all indicators into a few factors."
  - name: "Quarterly-RNN"
    tag: "comparison"
    text: "The same kind of network, but with quarterly averages only."
  - name: "Repeat-RNN"
    tag: "own design"
    own: true
    text: "Reads every month and repeats the latest quarterly figure."
  - name: "Multilayer-RNN"
    tag: "own design"
    own: true
    text: "A quarterly layer with a monthly layer on top."
  - name: "Alternate-RNN"
    tag: "own design"
    own: true
    text: "Monthly and quarterly networks take turns and share their memory."
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

{% include slide.html kicker="Problem" title="How is the economy doing right now?" text="The GDP figure arrives weeks after a quarter ends. Can a model use the monthly figures already in to estimate this quarter's growth?" src="/assets/img/projects/scriptie_probleem_en.svg" alt="Timeline: monthly figures arrive every month, but first-quarter GDP is only known weeks after the quarter ends" full=true %}

{% include data.html kicker="Data" title="Monthly and quarterly figures mixed" text="121 monthly and 117 quarterly indicators of the US economy, 1960–2024." src="/assets/img/projects/scriptie_bbp_groei_en.png" alt="Line chart of quarterly US GDP growth 1960–2024, with sharp drops in recessions" %}

{% include models.html kicker="Models" title="Two benchmarks, three own designs" text="LSTM and GRU are networks with a memory for time series. I adapted them to read monthly and quarterly data at the same time." %}

{% include slide.html kicker="Method" title="From raw series to nowcast" text="Retrained every year on all data so far and tested on the following year, as it would work in practice." src="/assets/img/projects/scriptie_pipeline_en.svg" alt="Pipeline: monthly and quarterly data, making stationary and feature selection, a mixed-frequency RNN and as output this quarter's GDP growth" full=true %}

{% include slide.html kicker="Results" title="11% more accurate than central banks" text="From 2000 to 2019 my networks (blue) beat every benchmark, including ARMA (−23%)." src="/assets/img/projects/scriptie_rmse_vergelijking_en.png" alt="Bar chart: Repeat-LSTM and Alternate-GRU have a lower error than Quarterly-GRU, the Dynamic Factor Model and ARMA" %}

{% include slide.html kicker="Evaluation" title="More complex is not always better" text="In crises, exactly when it matters, the difference with the central-bank model was not significant. That contradicts earlier research." statement=true %}
