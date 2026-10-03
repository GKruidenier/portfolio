---
layout: project
lang: en
ref: bachelor-thesis
project: bachelor-thesis
section: bachelor
title: "Bachelor's thesis: combination therapies with glutamine metabolism inhibitors"
lead: "Which drug combinations break cancer cells' resistance to glutamine metabolism inhibitors?"
description: Literature review of combination therapies that can break cancer cells' resistance to glutamine metabolism inhibitors.
abstract: "Many tumours run on the amino acid glutamine, but drugs that block it lose their effect as soon as cancer cells find a detour. In this literature review I mapped those detours and the combinations that can close them: a glutaminase inhibitor together with metabolic inhibitors, radiotherapy or immunotherapy."
abstract_image: /assets/img/projects/bachelor_abstract_en.svg
abstract_alt: "Visual summary in three steps: a tumour cell runs on glutamine; with one inhibitor it detours via glucose and fatty acids; a combination therapy blocks all routes and adds radiotherapy and T cells (immunotherapy)"
image: /assets/img/projects/bachelor_combinatietherapie.png
course: BSc Biomedical Sciences, Utrecht University, 2023
team: Individual literature review
tools: [Literature research, Cancer metabolism, Immunotherapy, Scientific writing]
---

<section class="slide slide--full chapter">
  <div class="slide__text">
    <p class="slide__num"><span class="slide__kicker">Glutamine metabolism</span></p>
    <h2>Tumours run on glutamine</h2>
  </div>
  <div class="chapter__body">
<div class="chapter__text">
<p>Cancer cells divide quickly and need a lot of energy and building material to do so. For a long time the focus was on glucose (the Warburg effect), but it is now clear that many tumours depend at least as much on the amino acid <strong>glutamine</strong>. Healthy cells make it themselves; tumour cells take large amounts from the blood, through transporters such as SLC1A5.</p>
<p>Inside the cell, the enzyme <strong>glutaminase (GLS)</strong> converts glutamine into glutamate and then into α-ketoglutarate. That enters the TCA cycle, the engine that supplies the cell with energy. Glutamine also provides three things a tumour needs:</p>
<ul class="chapter__list">
<li><strong>Building blocks.</strong> Nitrogen for DNA building blocks and other amino acids, and carbon for fatty acids and cell membranes. At least half of the non-essential amino acids in cancer cells come from glutamine.</li>
<li><strong>Protection.</strong> Glutamate is needed for glutathione, the cell's main antioxidant, which keeps harmful oxygen radicals (ROS) in check.</li>
<li><strong>Growth signal.</strong> Glutamine switches on mTORC1, a central switch for cell growth.</li>
</ul>
</div>
<figure class="chapter__figure chapter__figure--wide">
  <a href="{{ '/assets/img/projects/bachelor_glutamine_rollen_en.svg' | relative_url }}"><img src="{{ '/assets/img/projects/bachelor_glutamine_rollen_en.svg' | relative_url }}" alt="Diagram of a cancer cell: glutamine enters through SLC1A5, glutaminase converts it to glutamate and α-ketoglutarate for the TCA cycle; glutamine also provides building blocks, protection via glutathione and a growth signal via mTORC1" loading="lazy"></a>
  <figcaption>What glutamine does in a cancer cell, simplified. Glutaminase (GLS) is the target of the inhibitors. Own figure.</figcaption>
</figure>
<p class="chapter__note">Cancer genes strengthen this dependence: c-MYC (active in more than 70% of tumours) and KRAS increase glutamine uptake and the amount of glutaminase. That makes glutaminase an attractive target. The inhibitor <strong>CB-839</strong> is the only one tested in clinical trials so far, but on its own it was disappointing.</p>
  </div>
</section>

<section class="slide slide--full chapter">
  <div class="slide__text">
    <p class="slide__num"><span class="slide__kicker">Resistance</span></p>
    <h2>The cancer cell takes a detour</h2>
  </div>
  <div class="chapter__body">
<p class="chapter__lead">Blocking glutamine slows growth, but often does not kill the cancer cell. The cell switches to other routes to keep the TCA cycle running and keep making building blocks. In the literature I found five such detours.</p>
<div class="chapter__cols">
<ol class="routes">
<li class="routes__item routes__item--pink"><strong>Glucose instead of glutamine.</strong> Through glycolysis, glucose supplies the fuel. In mice the engine kept running after glutaminase was switched off; only when glucose processing was blocked as well did almost 40% of the mice develop no tumours.</li>
<li class="routes__item routes__item--green"><strong>Burning fatty acids.</strong> Pancreatic and breast cancer cells that became resistant to CB-839 burned more fatty acids via the enzyme CPT1.</li>
<li class="routes__item routes__item--purple"><strong>Glutamate by another route.</strong> Through the glutaminase II pathway or from the molecule NAAG, using the enzyme GCPII.</li>
<li class="routes__item routes__item--grey"><strong>Eating itself.</strong> In autophagy the cell breaks down its own parts to recycle building blocks. Blocking glutamine can actually switch this on.</li>
<li class="routes__item routes__item--blue"><strong>Taking up other amino acids.</strong> Extra transporters bring in aspartate (SLC1A3) and arginine (SLC7A3).</li>
</ol>
<figure class="chapter__figure">
  <a href="{{ '/assets/img/projects/bachelor_glutamineroutes.png' | relative_url }}"><img src="{{ '/assets/img/projects/bachelor_glutamineroutes.png' | relative_url }}" alt="Diagram of a cancer cell with the compensatory routes: glycolysis, fatty acid oxidation, the glutaminase II pathway, NAAG to glutamate and uptake of aspartate and arginine, with the inhibitors per route" loading="lazy"></a>
  <figcaption>The detours in one cell. Pink: glycolysis; green: fatty acid oxidation; purple: glutaminase II pathway; orange: NAAG to glutamate; blue: uptake of aspartate and arginine. Red: inhibitors that block these routes. Figure from my thesis, made with BioRender.</figcaption>
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
<p class="chapter__lead">Because a cancer cell has so many ways out, the answer lies in combinations: a glutaminase inhibitor together with one partner that closes exactly that exit or exploits a weak spot. I compared three such combinations. They are alternatives, not one treatment with all three at once.</p>
<p class="therapy__intro"><strong>Glutaminase inhibitor + one partner.</strong> <span>Hover over a therapy or tap it for the explanation and figure.</span></p>
<div class="therapy" data-therapy>
<div class="therapy__tabs" role="tablist">
<button type="button" class="therapy__tab therapy__tab--red is-active" role="tab" id="tab-met" aria-controls="pane-met" aria-selected="true"><span class="therapy__plus">+</span><span><strong>Metabolic inhibitors</strong><small>close glucose, mTOR and fatty acids</small></span></button>
<button type="button" class="therapy__tab therapy__tab--purple" role="tab" id="tab-rad" aria-controls="pane-rad" aria-selected="false"><span class="therapy__plus">+</span><span><strong>Radiotherapy</strong><small>more oxidative stress</small></span></button>
<button type="button" class="therapy__tab therapy__tab--blue" role="tab" id="tab-imm" aria-controls="pane-imm" aria-selected="false"><span class="therapy__plus">+</span><span><strong>Immunotherapy</strong><small>puts T cells back to work</small></span></button>
</div>
<div class="therapy__pane therapy__pane--red is-active" role="tabpanel" id="pane-met" aria-labelledby="tab-met">
<div class="therapy__text"><p>Block the detours themselves: metformin or Glutor reduce glucose use, MLN128 and everolimus inhibit mTOR, etomoxir blocks fatty acid burning and 2-PMPA the production of glutamate from NAAG. In animal models such combinations slowed tumour growth more than either drug alone.</p><p class="therapy__note">Caveat: cabozantinib worked in the lab, but added nothing in a first clinical trial in kidney cancer.</p></div>
<figure class="chapter__figure">
  <a href="{{ '/assets/img/projects/bachelor_combinatietherapie.png' | relative_url }}"><img src="{{ '/assets/img/projects/bachelor_combinatietherapie.png' | relative_url }}" alt="Diagram of a cancer cell showing where metabolic inhibitors act alongside glutaminase inhibitors" loading="lazy"></a>
  <figcaption>In red, the inhibitors that worked together with a glutaminase inhibitor: on glucose uptake, mTOR, fatty acid burning and the glutamate routes. Figure from my thesis.</figcaption>
</figure>
</div>
<div class="therapy__pane therapy__pane--purple" role="tabpanel" id="pane-rad" aria-labelledby="tab-rad">
<div class="therapy__text"><p>High oxidative stress predicts sensitivity better than glutamine use. Tumours with an overactive NRF2 protection pathway, for example through KEAP1, KRAS or IDH mutations, are therefore good candidates.</p><p>A glutaminase inhibitor lowers glutathione, so radiation hits harder: lung cancer cells became more sensitive to radiotherapy and in head and neck cancer CB-839 plus radiation gave a stronger response.</p></div>
<figure class="chapter__figure">
  <a href="{{ '/assets/img/projects/bachelor_oxidatieve_stress.png' | relative_url }}"><img src="{{ '/assets/img/projects/bachelor_oxidatieve_stress.png' | relative_url }}" alt="Diagram of the factors that raise oxidative stress, such as radiotherapy, KRAS and IDH mutations, and the NRF2 pathway that protects the cell" loading="lazy"></a>
  <figcaption>Radiotherapy and certain mutations raise oxidative stress (ROS); glutathione (GSH) made from glutamate absorbs it. Figure from my thesis, made with BioRender.</figcaption>
</figure>
</div>
<div class="therapy__pane therapy__pane--blue" role="tabpanel" id="pane-imm" aria-labelledby="tab-imm">
<div class="therapy__text"><p>Glutamine inhibitors can strengthen the immune response against cancer: L-DON and its variant JHU083 activate T cells, and L-DON makes pancreatic cancer easier for T cells to reach.</p><p>But blocking glutamine can also raise the protein PD-L1 on the tumour, which holds T cells back. A checkpoint inhibitor (anti-PD-L1) shields that protein. Together they worked better than either alone.</p></div>
<figure class="chapter__figure">
  <a href="{{ '/assets/img/projects/bachelor_immuuntherapie_en.svg' | relative_url }}"><img src="{{ '/assets/img/projects/bachelor_immuuntherapie_en.svg' | relative_url }}" alt="Two panels: on the left PD-L1 on the tumour cell inhibits the T cell; on the right an antibody shields PD-L1 and the T cell attacks the tumour cell" loading="lazy"></a>
  <figcaption>Left: after blocking glutamine, PD-L1 holds the T cell back. Right: with anti-PD-L1 the T cell attacks the tumour cell. Own figure.</figcaption>
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
<p class="chapter__conclusion"><strong>Conclusion:</strong> blocking glutamine metabolism alone is not enough. The future lies in combinations that target several routes at once, so the cancer cell has no way out.</p>
  </div>
</section>
