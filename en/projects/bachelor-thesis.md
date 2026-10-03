---
layout: project
lang: en
ref: bachelor-thesis
project: bachelor-thesis
section: bachelor
title: "Bachelor's thesis: combination therapies with glutamine metabolism inhibitors"
lead: "Which drug combinations break cancer cells' resistance to glutamine metabolism inhibitors?"
description: Literature review of combination therapies that can break cancer cells' resistance to glutamine metabolism inhibitors.
abstract: "Many tumours run on glutamine, but inhibitors lose their effect as soon as cancer cells find a detour. In this literature review I mapped those detours and the combination therapies that can close them, from metabolic inhibitors to radiotherapy and immunotherapy."
image: /assets/img/projects/bachelor_combinatietherapie.png
course: BSc Biomedical Sciences, Utrecht University, 2023
team: Individual literature review
tools: [Literature research, Cancer metabolism, Immunotherapy, Scientific writing]
models:
  - name: "Glutaminase inhibitors"
    tag: "basis"
    text: "Block the first step in glutamine breakdown, for example CB-839."
  - name: "Metabolic inhibitors"
    tag: "combination"
    own: true
    text: "Inhibit glucose uptake, mTOR or fatty acid oxidation, so the cell cannot switch routes."
  - name: "Radiotherapy"
    tag: "combination"
    own: true
    text: "Raises the oxidative stress that glutamine inhibitors exploit."
  - name: "Immunotherapy"
    tag: "combination"
    own: true
    text: "Checkpoint inhibitors; glutamine inhibitors can strengthen the immune response against cancer."
---

{% include slide.html kicker="Problem" title="Cancer cells find a detour" text="Many cancer cells depend on the amino acid glutamine to grow. Drugs that block it are promising, but cancer cells switch to other routes and become resistant. Which drug combinations close those detours?" %}

{% include slide.html kicker="Background" title="A cancer cell's routes" text="Glutamine is broken down into fuel for the cell. Inhibitors block that route, but the cell can switch to glucose, fatty acids and other sources of glutamate." src="/assets/img/projects/bachelor_glutamineroutes.png" alt="Diagram of a cancer cell with the routes from glutamine, glucose, fatty acids and aspartate into the TCA cycle, and the inhibitors per route" %}

{% include models.html kicker="Models" title="Treatments I compared" text="A glutaminase inhibitor as the basis, combined with treatments that close the exits or exploit the cell's weak spots." %}

{% include slide.html kicker="Method" title="A literature review in six steps" text="A 35-page literature review: from the role of glutamine to the combinations tested in preclinical and clinical research." src="/assets/img/projects/bachelor_methode_en.svg" alt="Six-step method diagram: question, background, inhibitors, resistance, combinations and conclusion" full=true %}

{% include slide.html kicker="Findings" title="Oxidative stress as a weak spot" text="High oxidative stress predicts sensitivity to glutaminase inhibitors better than how much glutamine a tumour uses. Therapies that raise stress, such as radiotherapy, are therefore promising partners." src="/assets/img/projects/bachelor_oxidatieve_stress.png" alt="Diagram of glutathione production via cystine transport and the factors that raise or lower reactive oxygen species (ROS)" %}

{% include slide.html kicker="Findings" title="Closing the exits" text="Combinations with inhibitors of glucose uptake, mTOR and fatty acid oxidation block the routes the cell uses to escape." src="/assets/img/projects/bachelor_combinatietherapie.png" alt="Diagram of a cancer cell showing the targets of combination therapies alongside glutaminase inhibitors" %}

{% include slide.html kicker="Conclusion" title="Not one brake, but several" text="Blocking glutamine metabolism alone is not enough. The future lies in combinations that target several routes at once, possibly together with immunotherapy." statement=true %}

<div class="role" markdown="1">
## What I take into data science
Reading a lot of research critically, weighing conflicting results and writing up a complex story clearly.
</div>
