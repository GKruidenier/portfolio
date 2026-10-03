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
    label: "less forecast error than the central-bank model (2000–2019)"
  - value: "−23%"
    label: "less forecast error than a simple benchmark"
  - value: "3"
    label: "own network designs"
models:
  - name: "Simple benchmark"
    tag: "ARMA"
    text: "Predicts GDP from its own past only."
  - name: "Central-bank model"
    tag: "Dynamic Factor Model"
    text: "Summarises all indicators into a few underlying trends. The standard to beat."
  - name: "Network with quarterly figures only"
    tag: "comparison"
    text: "The same kind of network, but with monthly figures averaged per quarter first."
  - name: "My network 1: repeat"
    tag: "Repeat-RNN"
    own: true
    text: "Reads every month and remembers the latest quarterly figure."
  - name: "My network 2: two layers"
    tag: "Multilayer-RNN"
    own: true
    text: "One layer for the quarters, with a layer on top that reads along every month."
  - name: "My network 3: alternate"
    tag: "Alternate-RNN"
    own: true
    text: "A monthly and a quarterly network take turns and share their memory."
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

{% include models.html kicker="Models" title="Two benchmarks, three own designs" text="My networks have a memory for sequences over time (LSTM or GRU). I adapted them to read monthly and quarterly figures at the same time." %}

{% include slide.html kicker="Method" title="From raw figures to estimate" text="The model never sees figures from the future: every year it is retrained on all data so far and tested on the following year." src="/assets/img/projects/scriptie_pipeline_en.svg" alt="Pipeline: monthly and quarterly figures, removing trends and picking the best figures, an own network and as output this quarter's GDP growth" full=true %}

{% include slide.html kicker="Results" title="11% more accurate than central banks" text="From 2000 to 2019 my networks (blue) make a smaller error than every benchmark: 11% less than the central-bank model and 23% less than the simple benchmark." src="/assets/img/projects/scriptie_resultaat_en.svg" alt="Bar chart: with the central-bank model at 100, my networks score 89 and 90, the simple benchmark 115" full=true %}

{% include slide.html kicker="Evaluation" title="More complex is not always better" text="In crises, exactly when it matters, the difference with the central-bank model was not significant. That contradicts earlier research." statement=true %}
