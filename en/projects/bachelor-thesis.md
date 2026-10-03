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
abstract_image: /assets/img/projects/bachelor_abstract_en.svg
abstract_alt: "Visual summary in three steps: a tumour cell runs on glutamine; with one inhibitor it detours via glucose and fatty acids; a combination therapy blocks all routes and adds radiotherapy and T cells (immunotherapy)"
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
<p>Cancer cells divide quickly and need a lot of energy and building material to do so. For a long time the focus was on sugar (glucose), but many tumours turn out to depend at least as much on the amino acid <strong>glutamine</strong>, which they take up from the blood in large amounts through the transporter SLC1A5.</p>
<p>Inside the cell, the enzyme <strong>glutaminase (GLS)</strong> turns glutamine into glutamate. That is the fuel for the cell's power plant and also the raw material for:</p>
<ul class="chapter__list">
<li><strong>Building blocks</strong> for the DNA, proteins and cell wall of new cells.</li>
<li><strong>Protection:</strong> an antioxidant that mops up harmful substances in the cell.</li>
<li><strong>A growth signal</strong> that tells the cell to grow.</li>
</ul>
</div>
<figure class="chapter__figure chapter__figure--wide">
  <a href="{{ '/assets/img/projects/bachelor_glutamine_rollen_en.svg' | relative_url }}"><img src="{{ '/assets/img/projects/bachelor_glutamine_rollen_en.svg' | relative_url }}" alt="Diagram of a cancer cell: glutamine from the blood is turned by an enzyme into fuel for energy, and also provides building blocks, protection and a growth signal" loading="lazy"></a>
  <figcaption>What glutamine does in a cancer cell. Everything runs through glutaminase, the step the inhibitor CB-839 blocks. Own figure.</figcaption>
</figure>
  </div>
</section>

<section class="slide slide--full chapter">
  <div class="slide__text">
    <p class="slide__num"><span class="slide__kicker">Resistance</span></p>
    <h2>The cancer cell takes a detour</h2>
  </div>
  <div class="chapter__body">
<p class="chapter__lead">Well-known cancer genes push glutamine use even further. That is why glutaminase inhibitors were developed, such as <strong>CB-839</strong>, the only one tested in patients so far. On its own, however, it was disappointing. Why? Blocking glutamine slows growth, but often does not kill the cancer cell: the cell switches to other sources and keeps its energy and building blocks up. In the literature I found five such detours.</p>
<div class="chapter__cols">
<ol class="routes"><li class="routes__item routes__item--pink"><strong>Sugar instead of glutamine.</strong> Through glycolysis the cell burns more glucose. In mice the cell kept running without glutamine; only when sugar use was blocked as well did almost 40% of the mice develop no tumour.</li><li class="routes__item routes__item--green"><strong>Burning fat.</strong> Tumours that stopped responding to CB-839 burned more fatty acids via the enzyme CPT1.</li><li class="routes__item routes__item--purple"><strong>Another route to glutamate.</strong> The cell makes the next step after glutamine (glutamate) through the glutaminase II pathway or from the molecule NAAG.</li><li class="routes__item routes__item--grey"><strong>Recycling its own parts (autophagy).</strong> The cell breaks down its own parts to recover building blocks. Blocking glutamine can actually switch this on.</li><li class="routes__item routes__item--blue"><strong>Taking up other amino acids.</strong> Extra transporters bring in the amino acids aspartate and arginine.</li></ol>
<figure class="chapter__figure">
  <a href="{{ '/assets/img/projects/bachelor_omwegen_en.svg' | relative_url }}"><img src="{{ '/assets/img/projects/bachelor_omwegen_en.svg' | relative_url }}" alt="Diagram of a cancer cell in which glutamine is blocked by CB-839, while glucose, fatty acids, another route to glutamate, recycling and other amino acids keep the energy going" loading="lazy"></a>
  <figcaption>Glutamine is blocked, but five detours keep the cell's energy going. The numbers match the list. Own figure.</figcaption>
</figure>
</div>
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
<button type="button" class="therapy__tab therapy__tab--blue" role="tab" id="tab-imm" aria-controls="pane-imm" aria-selected="false"><span class="therapy__plus">+</span><span><strong>Immunotherapy</strong><small>puts T cells back to work</small></span></button>
</div>
<div class="therapy__pane therapy__pane--red is-active" role="tabpanel" id="pane-met" aria-labelledby="tab-met">
<div class="therapy__text"><p>Inhibitors that also block the other fuel routes: the use of sugar, the burning of fat and the other route to glutamate. Without detours the engine stops. In animal models such combinations slowed tumour growth more than either drug alone.</p><p class="therapy__note">Not everything held up: one combination that worked in the lab added nothing in patients with kidney cancer.</p></div>
<figure class="chapter__figure">
  <a href="{{ '/assets/img/projects/bachelor_metabole_remmers_en.svg' | relative_url }}"><img src="{{ '/assets/img/projects/bachelor_metabole_remmers_en.svg' | relative_url }}" alt="Diagram of a cancer cell in which glutamine, glucose, fatty acids and the other route to glutamate are all blocked, so the energy fails" loading="lazy"></a>
  <figcaption>Glutamine and the detours blocked: the cell runs out of fuel. Own figure.</figcaption>
</figure>
</div>
<div class="therapy__pane therapy__pane--purple" role="tabpanel" id="pane-rad" aria-labelledby="tab-rad">
<div class="therapy__text"><p>Glutamine supplies the raw material for an antioxidant: the shield the tumour uses to protect itself against harmful substances. Tumours that rely heavily on that shield are the most sensitive to the inhibitor.</p><p>Once the shield is gone, radiation hits harder. In studies in lung and head and neck cancer the combination worked better than either alone.</p></div>
<figure class="chapter__figure">
  <a href="{{ '/assets/img/projects/bachelor_radiotherapie_en.svg' | relative_url }}"><img src="{{ '/assets/img/projects/bachelor_radiotherapie_en.svg' | relative_url }}" alt="Two panels: on the left a shield made from glutamine protects the tumour cell against harmful substances; on the right glutamine is blocked, the shield falls away and radiation damages the cell" loading="lazy"></a>
  <figcaption>Left: glutamine supplies the shield. Right: without the shield, radiation breaks the cell. Own figure.</figcaption>
</figure>
</div>
<div class="therapy__pane therapy__pane--blue" role="tabpanel" id="pane-imm" aria-labelledby="tab-imm">
<div class="therapy__text"><p>Blocking glutamine can help the immune system: immune cells (T cells) become more active and reach the tumour more easily.</p><p>But the tumour responds by putting more brake proteins on its surface, which hold T cells back. An immunotherapy that blocks that brake solves this. Together they worked better than either alone.</p></div>
<figure class="chapter__figure">
  <a href="{{ '/assets/img/projects/bachelor_immuuntherapie_en.svg' | relative_url }}"><img src="{{ '/assets/img/projects/bachelor_immuuntherapie_en.svg' | relative_url }}" alt="Two panels: on the left brake proteins on the tumour cell hold the T cell back; on the right a drug blocks the brake and the T cell attacks the tumour cell" loading="lazy"></a>
  <figcaption>Left: brake proteins hold the T cell back. Right: a drug blocks the brake and the T cell attacks. Own figure.</figcaption>
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
