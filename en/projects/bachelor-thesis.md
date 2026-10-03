---
layout: project
lang: en
ref: bachelor-thesis
project: bachelor-thesis
section: bachelor
title: "Bachelor's thesis: combination therapies with glutamine metabolism inhibitors"
lead: "Which drug combinations break cancer cells' resistance to glutamine metabolism inhibitors?"
description: Literature review of combination therapies that can break cancer cells' resistance to glutamine metabolism inhibitors.
abstract: "Many tumours run on glutamine, but inhibitors lose their effect as soon as cancer cells find a detour. In this literature review I mapped those detours and the drug combinations that can close them."
abstract_image: /assets/img/projects/bachelor_abstract_en.svg
abstract_alt: "Visual summary in three steps: a tumour cell runs on glutamine; with one inhibitor it detours via glucose and fatty acids; a combination of inhibitors closes the detours too"
image: /assets/img/projects/bachelor_combinatietherapie.png
course: BSc Biomedical Sciences, Utrecht University, 2023
team: Individual literature review
tools: [Literature research, Cancer metabolism, Immunotherapy, Scientific writing]
models:
  - name: "Glutaminase inhibitors"
    tag: "basis"
    text: "Block the breakdown of glutamine, such as CB-839."
  - name: "Metabolic inhibitors"
    tag: "combination"
    own: true
    text: "Inhibit glucose uptake, mTOR or fatty acid oxidation."
  - name: "Radiotherapy"
    tag: "combination"
    own: true
    text: "Raises the oxidative stress the cell is sensitive to."
  - name: "Immunotherapy"
    tag: "combination"
    own: true
    text: "Checkpoint inhibitors, strengthened by glutamine inhibitors."
---

{% include slide.html kicker="Problem" title="Cancer cells find a detour" text="Glutamine metabolism inhibitors are promising, but tumours become resistant by switching to other routes. Which combinations break through that?" src="/assets/img/projects/bachelor_glutamineroutes.png" alt="Diagram of a cancer cell with the routes from glutamine, glucose and fatty acids into the TCA cycle, and the inhibitors per route" %}

{% include models.html kicker="Treatments" title="Treatments I compared" text="A glutaminase inhibitor as the basis, combined with treatments that close the exits." %}

{% include slide.html kicker="Method" title="A 35-page literature review" text="From the role of glutamine through resistance to the combinations tested in preclinical and clinical research." src="/assets/img/projects/bachelor_pipeline_en.svg" alt="Diagram: preclinical and clinical research, analysed for the role of glutamine, resistance and combinations, weighed into the conclusion" full=true %}

{% include slide.html kicker="Findings" title="Two weak spots" text="High oxidative stress predicts sensitivity better than glutamine use. And inhibitors of glucose, mTOR and fatty acids close the escape routes." src="/assets/img/projects/bachelor_oxidatieve_stress.png" alt="Diagram of the factors that raise or lower oxidative stress in the cell" src2="/assets/img/projects/bachelor_combinatietherapie.png" alt2="Diagram of a cancer cell showing the targets of combination therapies" full=true %}

{% include slide.html kicker="Conclusion" title="Not one brake, but several" text="The future lies in combinations that target several routes at once, possibly together with immunotherapy." statement=true %}

<div class="role" markdown="1">
## What I take into data science
Reading a lot of research critically, weighing conflicting results and writing up a complex story clearly.
</div>
