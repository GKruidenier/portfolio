---
layout: project
lang: en
ref: thesis
project: thesis
section: master
title: "Master's thesis: nowcasting economic growth with deep learning"
lead: Can neural networks that combine monthly and quarterly data directly 'nowcast' the economy better than the models central banks use?
description: Three custom LSTM and GRU architectures for nowcasting GDP growth, tested against Dynamic Factor Models and ARMA.
image: /assets/img/projects/scriptie_rmse_vergelijking_en.png
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

## The question

Official GDP figures are published only once a quarter and with a long delay, while policymakers and markets want to know how the economy is doing right now. Can deep-learning models that combine monthly and quarterly data directly give a better real-time estimate (a nowcast)?

## The data

The FRED-MD and FRED-QD datasets from the Federal Reserve Bank of St. Louis: hundreds of monthly and quarterly economic indicators for the United States.

## Approach

I designed three neural-network architectures, built on LSTM and GRU, that process data of different frequencies directly, without first averaging it or filling in missing values. I tested them against the models central banks use for this task (Dynamic Factor Models and ARMA) and against networks that only see quarterly data.

{% include figure.html src="/assets/img/projects/scriptie_methode_stroomschema.png" alt="Flow chart of the research design" caption="Research design: the models are retrained year by year on all data up to that point and tested on the following year, up to 2024. They are then evaluated on the full period, on 2000–2019 and on recessions." narrow=true %}

## Results

{% include figure.html src="/assets/img/projects/scriptie_rmse_vergelijking_en.png" alt="Bar chart: my models Repeat-LSTM and Alternate-GRU have a lower RMSE than Quarterly-GRU, the Dynamic Factor Model and ARMA" caption="Error (RMSE) of the US nowcasts, 2000–2019. Lower is better; the blue bars are my own architectures." %}

- **From 2000 to 2019 my architectures beat every benchmark.** The best one has about 11% lower error than the Dynamic Factor Model and 23% lower than ARMA.
- Including the COVID years (2000–2024), Alternate-GRU still has the lowest error of all models.
- Not every variant improves as more monthly data arrives during the quarter: there is a trade-off between good predictions at the start and at the end of a quarter.
- During crises the models are not significantly better than the Dynamic Factor Model. This contradicts earlier research, which claimed that non-linear methods excel in exactly those periods.

{% include figure.html src="/assets/img/projects/scriptie_voorspelling_vs_werkelijk.png" alt="Line chart of predicted and actual GDP growth 2000–2019 for the Dynamic Factor Model and Alternate-GRU" caption="Predicted and actual GDP growth, 2000–2019, with recessions highlighted." wide=true %}

<div class="role" markdown="1">
## What I learned
A more complex model is not automatically better. In calm periods my networks clearly won, but in crises, when a good forecast matters most, the difference with the classic model was not significant. Showing that honestly mattered to me as much as the gain itself.
</div>
