---
layout: project
lang: en
ref: bachelor-thesis
project: bachelor-thesis
section: bachelor
title: "Bachelor's thesis: combination therapies with glutamine metabolism inhibitors"
lead: "Which drug combinations break cancer cells' resistance to glutamine metabolism inhibitors?"
description: Literature review of combination therapies that can break cancer cells' resistance to glutamine metabolism inhibitors.
abstract: "Many tumours run on the amino acid glutamine, but drugs that block it lose their effect as soon as cancer cells find a detour. In this literature review I mapped those detours and the combinations that can close them: a glutamine inhibitor together with other inhibitors, with radiation or with immunotherapy."
abstract_image: /assets/img/projects/bachelor_abstract_en_v2.svg
abstract_alt: "Visual summary in three steps: a tumour cell runs on glutamine; with one inhibitor (CB-839) it detours via glucose and fatty acids; a combination therapy pairs the glutamine inhibitor with one partner: other inhibitors, radiotherapy or immunotherapy"
image: /assets/img/projects/bachelor_abstract.png
course: BSc Biomedical Sciences, Utrecht University, 2023
team: Individual literature review
tools: [Literature research, Cancer metabolism, Immunotherapy, Scientific writing]
---

<section class="slide slide--full chapter">
  <div class="slide__text">
    <p class="slide__num"><span class="slide__kicker">Glutamine and cancer</span></p>
    <h2>Tumours run on glutamine</h2>
  </div>
  <div class="chapter__body">
<div class="chapter__text">
<p>Cancer cells divide quickly and need a lot of energy and building material to do so. For a long time the focus was on sugar (glucose), but many tumours turn out to depend at least as much on the amino acid glutamine, which they take up from the blood in large amounts through the transporter SLC1A5.</p>
<p>Inside the cell, the enzyme glutaminase (GLS) turns glutamine into glutamate. That is the fuel for the cell's power plant and also the raw material for:</p>
<ul class="chapter__list">
<li><strong>Building blocks</strong> for the DNA, proteins and cell wall of new cells.</li>
<li><strong>Protection:</strong> an antioxidant that mops up harmful substances in the cell.</li>
<li><strong>A growth signal</strong> that tells the cell to grow.</li>
</ul>
</div>
<figure class="chapter__figure chapter__figure--wide">
  <a href="{{ '/assets/img/projects/bachelor_glutamine_rollen_en_v2.svg' | relative_url }}"><img src="{{ '/assets/img/projects/bachelor_glutamine_rollen_en_v2.svg' | relative_url }}" alt="Diagram of a cancer cell: glutamine enters through SLC1A5 and glutaminase (GLS) turns it into glutamate, which feeds the TCA cycle for energy, the antioxidant glutathione (GSH) and the mTORC1 growth signal; glutamine also supplies nucleotides directly" loading="lazy"></a>
  <figcaption>What glutamine does in a cancer cell. Most routes run through glutaminase (GLS), the step the inhibitor CB-839 blocks. Own figure.</figcaption>
</figure>
  </div>
</section>

<section class="slide slide--full chapter">
  <div class="slide__text">
    <p class="slide__num"><span class="slide__kicker">Resistance</span></p>
    <h2>The cancer cell takes a detour</h2>
  </div>
  <div class="chapter__body">
<p class="chapter__lead">Well-known cancer genes push glutamine use even further. That is why glutaminase inhibitors were developed, such as CB-839, the only one tested in patients so far. On its own, however, it was disappointing. Why? Blocking glutamine slows growth, but often does not kill the cancer cell: the cell switches to other sources and keeps its energy and building blocks up. In the literature I found five such detours.</p>
<figure class="chapter__figure chapter__figure--cell">
  <a href="{{ '/assets/img/projects/bachelor_omwegen_en_v2.svg' | relative_url }}"><img src="{{ '/assets/img/projects/bachelor_omwegen_en_v2.svg' | relative_url }}" alt="Diagram of a cancer cell in which CB-839 blocks glutaminase, while glucose and fatty acids feed the TCA cycle, the glutaminase II pathway and NAAG make glutamate, and autophagy and uptake of aspartate and arginine supply building blocks and growth signals" loading="lazy"></a>
  <figcaption>Glutaminase is blocked, but five detours rejoin the cell's metabolism further on. The numbers match the list. Own figure.</figcaption>
</figure>
<ol class="routes routes--grid"><li class="routes__item routes__item--pink"><strong>Sugar instead of glutamine.</strong> Through glycolysis the cell burns more glucose. In mice the cell kept running without glutamine; only when sugar use was blocked as well did almost 40% of the mice develop no tumour.</li><li class="routes__item routes__item--green"><strong>Burning fat.</strong> Tumours that stopped responding to CB-839 burned more fatty acids via the enzyme carnitine palmitoyltransferase 1 (CPT1).</li><li class="routes__item routes__item--purple"><strong>Another route to glutamate.</strong> The cell makes the next step after glutamine (glutamate) through the glutaminase II pathway or from the molecule N-acetylaspartylglutamate (NAAG).</li><li class="routes__item routes__item--grey"><strong>Recycling its own parts (autophagy).</strong> The cell breaks down its own parts to recover building blocks. Blocking glutamine can actually switch this on.</li><li class="routes__item routes__item--blue"><strong>Taking up other amino acids.</strong> Extra transporters bring in the amino acids aspartate and arginine.</li></ol>
  </div>
</section>

<section class="slide slide--full chapter">
  <div class="slide__text">
    <p class="slide__num"><span class="slide__kicker">Combination therapies</span></p>
    <h2>Closing the detours</h2>
  </div>
  <div class="chapter__body">
<p class="chapter__lead">Because a cancer cell has so many ways out, the answer lies in combinations: a glutamine inhibitor together with one partner that closes an exit or exploits a weak spot. I compared three such combinations. They are alternatives, not one treatment with all three at once.</p>
<p class="therapy__intro"><strong>Glutamine inhibitor + one partner.</strong> <span>Hover over a therapy or tap it for the explanation and figure.</span></p>
<div class="therapy" data-therapy>
<div class="therapy__tabs" role="tablist">
<button type="button" class="therapy__tab therapy__tab--red is-active" role="tab" id="tab-met" aria-controls="pane-met" aria-selected="true"><span class="therapy__plus">+</span><span><strong>Other inhibitors</strong><small>close sugar, fat and glutamate</small></span></button>
<button type="button" class="therapy__tab therapy__tab--purple" role="tab" id="tab-rad" aria-controls="pane-rad" aria-selected="false"><span class="therapy__plus">+</span><span><strong>Radiation</strong><small>no shield, more damage</small></span></button>
<button type="button" class="therapy__tab therapy__tab--blue" role="tab" id="tab-imm" aria-controls="pane-imm" aria-selected="false"><span class="therapy__plus">+</span><span><strong>Immunotherapy</strong><small>stronger defence, brake off</small></span></button>
</div>
<div class="therapy__pane therapy__pane--red is-active" role="tabpanel" id="pane-met" aria-labelledby="tab-met">
<div class="therapy__text"><p>Inhibitors that also block the other fuel routes: the use of sugar, the burning of fat and the other route to glutamate. Without detours the engine stops. In animal models such combinations slowed tumour growth more than either drug alone.</p><p class="therapy__note">Not everything held up: one combination that worked in the lab added nothing in patients with kidney cancer.</p></div>
<figure class="chapter__figure">
  <a href="{{ '/assets/img/projects/bachelor_metabole_remmers_en_v2.svg' | relative_url }}"><img src="{{ '/assets/img/projects/bachelor_metabole_remmers_en_v2.svg' | relative_url }}" alt="The same cancer cell with the detours closed: metformin, etomoxir, GTK knockdown and 2-PMPA block glycolysis, fatty acid oxidation and the other routes to glutamate, so the TCA cycle runs out of fuel; autophagy and amino-acid uptake are not targeted" loading="lazy"></a>
  <figcaption>The same cell with the detours closed: metformin, etomoxir, 2-PMPA and GTK knockdown block the routes, so the TCA cycle runs out of fuel. Routes 4 and 5 (faded) are not targeted. Own figure.</figcaption>
</figure>
</div>
<div class="therapy__pane therapy__pane--purple" role="tabpanel" id="pane-rad" aria-labelledby="tab-rad">
<div class="therapy__text"><p>Glutamine supplies the raw material for an antioxidant: the shield the tumour uses to protect itself against harmful substances. Tumours that rely heavily on that shield are the most sensitive to the inhibitor.</p><p>Once the shield is gone, radiation hits harder. In studies in lung and head and neck cancer the combination worked better than either alone.</p></div>
<figure class="chapter__figure">
  <a href="{{ '/assets/img/projects/bachelor_radiotherapie_en_v2.svg' | relative_url }}"><img src="{{ '/assets/img/projects/bachelor_radiotherapie_en_v2.svg' | relative_url }}" alt="Two cancer cells get the same radiation. Left: glutamine supplies glutathione (GSH), which neutralises the reactive oxygen species (ROS). Right: CB-839 blocks glutamine, there is no GSH and the ROS build up" loading="lazy"></a>
  <figcaption>Same radiation, one difference. Left: glutamine supplies glutathione (GSH), which neutralises the reactive oxygen species (ROS). Right: CB-839 removes that shield and the ROS build up. Own figure.</figcaption>
</figure>
</div>
<div class="therapy__pane therapy__pane--blue" role="tabpanel" id="pane-imm" aria-labelledby="tab-imm">
<div class="therapy__text"><p>Blocking glutamine actually makes the immune response against the tumour stronger. Immune cells (T cells) are more flexible than tumour cells: without glutamine they switch to other fuels and become more active, while the tumour starves. There are also fewer cells around the tumour that hold the immune response back.</p><p>But blocking glutamine can also raise the brake protein on the tumour. A checkpoint inhibitor removes that brake, so the extra-active T cells can do their job. Together this worked better than either drug alone.</p></div>
<figure class="chapter__figure">
  <a href="{{ '/assets/img/projects/bachelor_immuuntherapie_en_v2.svg' | relative_url }}"><img src="{{ '/assets/img/projects/bachelor_immuuntherapie_en_v2.svg' | relative_url }}" alt="Three steps: a glutamine inhibitor starves the tumour cell while the CD8+ T cell switches fuel and gets stronger; the tumour cell puts more PD-L1 on its surface, which binds PD-1 and switches the T cell off; a checkpoint inhibitor (anti-PD-L1) blocks PD-L1 so the T cell attacks" loading="lazy"></a>
  <figcaption>1: blocking glutamine starves the tumour cell and strengthens the CD8+ T cell. 2: the tumour cell answers with more PD-L1, which switches the T cell off through PD-1. 3: a checkpoint inhibitor (anti-PD-L1) blocks that brake. Own figure.</figcaption>
</figure>
</div>
</div>
<script>
(function () {
  document.querySelectorAll('[data-therapy]').forEach(function (box) {
    var tabs = box.querySelectorAll('.therapy__tab');
    function show(tab) {
      tabs.forEach(function (t) {
        var on = t === tab;
        t.classList.toggle('is-active', on);
        t.setAttribute('aria-selected', on ? 'true' : 'false');
        box.querySelector('#' + t.getAttribute('aria-controls')).classList.toggle('is-active', on);
      });
    }
    tabs.forEach(function (t) {
      t.addEventListener('mouseenter', function () { show(t); });
      t.addEventListener('focus', function () { show(t); });
      t.addEventListener('click', function () { show(t); });
    });
    box.classList.add('is-ready');
  });
})();
</script>
<p class="chapter__conclusion"><strong>Conclusion:</strong> blocking glutamine alone is not enough. The future lies in combinations that target several routes at once, so the cancer cell has no way out.</p>
  </div>
</section>
