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
abstract: "GDP is published quarterly and with a delay, while monthly figures arrive much sooner. I designed three neural networks that combine both directly. From 2000 to 2019 their forecast error is about 10% lower than that of a Dynamic Factor Model: the type of model central banks use, which I applied in a simple form to the same data."
abstract_image: /assets/img/projects/scriptie_concept_en.svg
abstract_alt: "Visual summary: monthly and quarterly data feed a custom network that estimates GDP growth for the current quarter"
course: MSc Data Science and Society, Tilburg University
team: Individual research
code: https://github.com/GKruidenier/GDP-nowcasting-thesis
tools: [Python, PyTorch, LSTM, GRU, statsmodels, Dynamic Factor Models, ARMA]
stats:
  - value: "−10%"
    label: "less forecast error than a Dynamic Factor Model on the same data (2000–2019)"
  - value: "−4%"
    label: "less forecast error when the network also reads the monthly figures"
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

{% include slide.html kicker="Background" title="Existing models, two new questions" text="Almost every central bank has a nowcasting model, usually a Dynamic Factor Model. Machine learning has only been tested in academic studies, and deep learning for GDP in just a handful. Moreover, those studies first average the monthly figures into quarters, which loses information. To keep the monthly figures, I had to adapt the architecture of the networks." src="/assets/img/projects/scriptie_aanleiding_en.svg" alt="From classic models (Dynamic Factor Model, used by almost every central bank) via machine learning (monthly figures averaged first) to deep learning that reads monthly and quarterly figures directly. Research question 1: can deep learning nowcast GDP and how does it perform against the classic models? Research question 2: does the estimate for the current quarter improve when the model also reads the monthly figures?" full=true %}

{% include data.html kicker="Data" title="Monthly and quarterly figures mixed" text="121 monthly and 117 quarterly indicators of the US economy, 1960–2024." src="/assets/img/projects/scriptie_bbp_groei_en.png" alt="Line chart of quarterly US GDP growth 1960–2024, with sharp drops in recessions" %}

{% include slide.html kicker="Models" title="Three ways to combine month and quarter" text="All models get the same figures. My networks (LSTM and GRU) have a memory and step through time. The difference is how monthly and quarterly figures come together." src="/assets/img/projects/scriptie_modellen_en.svg" alt="Six models. Benchmarks: the classic time-series model ARMA uses only the past of GDP, a simple version of the central banks' Dynamic Factor Model sums up the figures in a few trends, and a network on quarterly data averages the monthly figures first. My designs: repeat (one step per month, the quarterly figure is read along), two layers (a quarterly layer feeds a monthly layer) and alternate (quarterly and monthly network take turns with one shared memory)" full=true %}

{% include slide.html kicker="Result question 1" title="Deep learning forecasts better than the classic models" text="From 2000 to 2019, my deep learning models that combine monthly and quarterly figures made a forecast error about 10% smaller than the Dynamic Factor Model, and over 20% smaller than the time-series model ARMA." src="/assets/img/projects/scriptie_echt_vs_voorspeld_en.svg" alt="Line chart of actual and estimated GDP growth per quarter, 2000–2019. The deep learning line follows actual growth most closely, including in the 2008–2009 recession. Average deviation: ARMA 0.58, Dynamic Factor Model 0.50, deep learning 0.45 percentage points." full=true %}

{% include slide.html kicker="Result question 2" title="Reading the monthly figures improves the estimate" text="The same type of network makes a 4% smaller error when it reads the monthly figures as well as the quarterly ones." src="/assets/img/projects/scriptie_resultaat_vraag2_en.svg" alt="Bar chart of how far the estimate is from actual GDP growth on average: deep learning on quarterly figures only is off by 0.47 percentage points on average, deep learning with monthly and quarterly figures by 0.45. That is 4% less." full=true %}

{% include slide.html kicker="Evaluation" title="What can be better, and what it does not say" text="Surprisingly, for most models the estimate first got worse after the first new monthly figure. Only the alternating GRU network improved every month. In crises my networks were not significantly better than the Dynamic Factor Model, unlike what earlier research found. And my Dynamic Factor Model is a simple version on the same data. Central banks use a far more extensive version, so this says nothing about their nowcasts." statement=true %}
