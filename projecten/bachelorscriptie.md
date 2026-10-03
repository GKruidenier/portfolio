---
layout: project
lang: nl
ref: bachelor-thesis
project: bachelor-thesis
section: bachelor
title: "Bachelorscriptie: combinatietherapieën met glutaminemetabolismeremmers"
lead: "Welke medicijncombinaties doorbreken de resistentie van kankercellen tegen glutaminemetabolismeremmers?"
description: Literatuurstudie naar combinatietherapieën die de resistentie van kankercellen tegen glutaminemetabolismeremmers kunnen doorbreken.
abstract: "Veel tumoren draaien op het aminozuur glutamine, maar medicijnen die dat blokkeren verliezen hun werking zodra kankercellen een omweg vinden. In deze literatuurstudie bracht ik die omwegen in kaart en welke combinaties ze kunnen afsluiten: een glutaminaseremmer samen met metabole remmers, radiotherapie of immuuntherapie."
abstract_image: /assets/img/projects/bachelor_abstract.svg
abstract_alt: "Visuele samenvatting in drie stappen: een tumorcel draait op glutamine; met één remmer neemt de cel een omweg via glucose en vetzuren; een combinatietherapie remt alle routes en zet daarnaast radiotherapie en T-cellen (immuuntherapie) in"
image: /assets/img/projects/bachelor_combinatietherapie.png
course: BSc Biomedische Wetenschappen, Universiteit Utrecht, 2023
team: Individuele literatuurstudie
tools: [Literatuuronderzoek, Kankermetabolisme, Immunotherapie, Wetenschappelijk schrijven]
---

<section class="slide slide--full chapter">
  <div class="slide__text">
    <p class="slide__num"><span class="slide__kicker">Glutaminemetabolisme</span></p>
    <h2>Tumoren draaien op glutamine</h2>
  </div>
  <div class="chapter__body">
<div class="chapter__text">
<p>Kankercellen delen snel en hebben daarvoor veel energie en bouwstoffen nodig. Lang lag de nadruk op glucose (het Warburg-effect), maar inmiddels is duidelijk dat veel tumoren minstens zo afhankelijk zijn van het aminozuur <strong>glutamine</strong>. Gezonde cellen maken het zelf; tumorcellen halen het in grote hoeveelheden uit het bloed, via transporters zoals SLC1A5.</p>
<p>In de cel zet het enzym <strong>glutaminase (GLS)</strong> glutamine om in glutamaat en daarna in α-ketoglutaraat. Dat gaat de citroenzuurcyclus in, de motor die de cel van energie voorziet. Daarnaast levert glutamine drie dingen die een tumor nodig heeft:</p>
<ul class="chapter__list">
<li><strong>Bouwstoffen.</strong> Stikstof voor DNA-bouwstenen en andere aminozuren, en koolstof voor vetzuren en celmembranen. Minstens de helft van de niet-essentiële aminozuren in kankercellen komt uit glutamine.</li>
<li><strong>Bescherming.</strong> Glutamaat is nodig voor glutathion, de belangrijkste antioxidant van de cel. Die houdt schadelijke zuurstofradicalen (ROS) in toom.</li>
<li><strong>Groeisignaal.</strong> Glutamine zet mTORC1 aan, een centrale schakelaar voor celgroei.</li>
</ul>
</div>
<figure class="chapter__figure chapter__figure--wide">
  <a href="{{ '/assets/img/projects/bachelor_glutamine_rollen.svg' | relative_url }}"><img src="{{ '/assets/img/projects/bachelor_glutamine_rollen.svg' | relative_url }}" alt="Schema van een kankercel: glutamine komt binnen via SLC1A5, glutaminase zet het om in glutamaat en α-ketoglutaraat voor de citroenzuurcyclus; glutamine levert ook bouwstoffen, bescherming via glutathion en een groeisignaal via mTORC1" loading="lazy"></a>
  <figcaption>Wat glutamine doet in een kankercel, vereenvoudigd. Glutaminase (GLS) is het doelwit van de remmers. Eigen figuur.</figcaption>
</figure>
<p class="chapter__note">Kankergenen versterken deze afhankelijkheid: c-MYC (actief in meer dan 70% van de tumoren) en KRAS verhogen de glutamineopname en de hoeveelheid glutaminase. Dat maakt glutaminase een aantrekkelijk doelwit. De remmer <strong>CB-839</strong> is als enige al in klinische studies getest, maar werkte als losse behandeling teleurstellend.</p>
  </div>
</section>

<section class="slide slide--full chapter">
  <div class="slide__text">
    <p class="slide__num"><span class="slide__kicker">Resistentie</span></p>
    <h2>De kankercel neemt een omweg</h2>
  </div>
  <div class="chapter__body">
<p class="chapter__lead">Glutamine remmen remt de groei, maar doodt de kankercel vaak niet. De cel schakelt over op andere routes om de citroenzuurcyclus draaiende te houden en zijn bouwstoffen te maken. In de literatuur vond ik vijf van zulke omwegen.</p>
<div class="chapter__cols">
<ol class="routes">
<li class="routes__item routes__item--pink"><strong>Glucose in plaats van glutamine.</strong> Via de glycolyse levert glucose de brandstof. In muizen bleef de motor draaien na het uitschakelen van glutaminase; pas toen ook de glucoseverwerking werd geblokkeerd, ontwikkelde bijna 40% van de muizen geen tumoren.</li>
<li class="routes__item routes__item--green"><strong>Vetzuren verbranden.</strong> Alvleesklier- en borstkankercellen die resistent werden tegen CB-839, verbrandden meer vetzuren via het enzym CPT1.</li>
<li class="routes__item routes__item--purple"><strong>Glutamaat langs een andere weg.</strong> Via de glutaminase II-route of uit de stof NAAG, met het enzym GCPII.</li>
<li class="routes__item routes__item--grey"><strong>Zichzelf opeten.</strong> Bij autofagie breekt de cel eigen onderdelen af om bouwstoffen te recyclen. Glutamine remmen kan dat juist aanzetten.</li>
<li class="routes__item routes__item--blue"><strong>Andere aminozuren opnemen.</strong> Extra transporters halen aspartaat (SLC1A3) en arginine (SLC7A3) binnen.</li>
</ol>
<figure class="chapter__figure">
  <a href="{{ '/assets/img/projects/bachelor_glutamineroutes.png' | relative_url }}"><img src="{{ '/assets/img/projects/bachelor_glutamineroutes.png' | relative_url }}" alt="Schema van een kankercel met de compensatieroutes: glycolyse, vetzuuroxidatie, de glutaminase II-route, NAAG naar glutamaat en opname van aspartaat en arginine, met per route de remmers" loading="lazy"></a>
  <figcaption>De omwegen in één cel. Roze: glycolyse; groen: vetzuuroxidatie; paars: glutaminase II-route; oranje: NAAG naar glutamaat; blauw: opname van aspartaat en arginine. Rood: remmers die deze routes blokkeren. Figuur uit mijn scriptie, gemaakt met BioRender.</figcaption>
</figure>
</div>
  </div>
</section>

<section class="slide slide--full chapter">
  <div class="slide__text">
    <p class="slide__num"><span class="slide__kicker">Combinatietherapieën</span></p>
    <h2>De omwegen afsluiten</h2>
  </div>
  <div class="chapter__body">
<p class="chapter__lead">Omdat een kankercel zoveel uitwegen heeft, ligt de oplossing in combinaties: een glutaminaseremmer samen met één partner die precies die uitweg dichtzet of een zwakke plek benut. Ik vergeleek drie van zulke combinaties. Het zijn alternatieven, geen behandeling met alle drie tegelijk.</p>
<p class="therapy__intro"><strong>Glutaminaseremmer + één partner.</strong> <span>Beweeg over een therapie of tik erop voor de uitleg en het plaatje.</span></p>
<div class="therapy" data-therapy>
<div class="therapy__tabs" role="tablist">
<button type="button" class="therapy__tab therapy__tab--red is-active" role="tab" id="tab-met" aria-controls="pane-met" aria-selected="true"><span class="therapy__plus">+</span><span><strong>Metabole remmers</strong><small>glucose, mTOR en vetzuren dicht</small></span></button>
<button type="button" class="therapy__tab therapy__tab--purple" role="tab" id="tab-rad" aria-controls="pane-rad" aria-selected="false"><span class="therapy__plus">+</span><span><strong>Radiotherapie</strong><small>meer oxidatieve stress</small></span></button>
<button type="button" class="therapy__tab therapy__tab--blue" role="tab" id="tab-imm" aria-controls="pane-imm" aria-selected="false"><span class="therapy__plus">+</span><span><strong>Immuuntherapie</strong><small>T-cellen weer aan het werk</small></span></button>
</div>
<div class="therapy__pane therapy__pane--red is-active" role="tabpanel" id="pane-met" aria-labelledby="tab-met">
<div class="therapy__text"><p>Blokkeren de omwegen zelf: metformine of Glutor remmen het glucosegebruik, MLN128 en everolimus remmen mTOR, etomoxir remt de vetzuurverbranding en 2-PMPA de aanmaak van glutamaat uit NAAG. In diermodellen remden zulke combinaties de tumorgroei sterker dan elk middel apart.</p><p class="therapy__note">Kanttekening: cabozantinib werkte in het lab, maar voegde in een eerste klinische studie bij nierkanker niets toe.</p></div>
<figure class="chapter__figure">
  <a href="{{ '/assets/img/projects/bachelor_combinatietherapie.png' | relative_url }}"><img src="{{ '/assets/img/projects/bachelor_combinatietherapie.png' | relative_url }}" alt="Schema van een kankercel met de aangrijpingspunten van metabole remmers naast glutaminaseremmers" loading="lazy"></a>
  <figcaption>In rood de remmers die samen met een glutaminaseremmer werkten: op glucoseopname, mTOR, vetzuurverbranding en de glutamaatroutes. Figuur uit mijn scriptie.</figcaption>
</figure>
</div>
<div class="therapy__pane therapy__pane--purple" role="tabpanel" id="pane-rad" aria-labelledby="tab-rad">
<div class="therapy__text"><p>Hoge oxidatieve stress voorspelt beter dan het glutaminegebruik of een tumor gevoelig is. Tumoren met een overactieve NRF2-beschermingsroute, bijvoorbeeld door KEAP1-, KRAS- of IDH-mutaties, zijn daarom goede kandidaten.</p><p>Een glutaminaseremmer verlaagt het glutathion, zodat bestraling harder aankomt: longkankercellen werden gevoeliger voor radiotherapie en bij hoofd-halskanker gaf CB-839 plus bestraling een sterkere respons.</p></div>
<figure class="chapter__figure">
  <a href="{{ '/assets/img/projects/bachelor_oxidatieve_stress.png' | relative_url }}"><img src="{{ '/assets/img/projects/bachelor_oxidatieve_stress.png' | relative_url }}" alt="Schema van de factoren die oxidatieve stress verhogen, zoals radiotherapie, KRAS- en IDH-mutaties, en de NRF2-route die de cel beschermt" loading="lazy"></a>
  <figcaption>Radiotherapie en bepaalde mutaties verhogen de oxidatieve stress (ROS); glutathion (GSH) uit glutamaat vangt die op. Figuur uit mijn scriptie, gemaakt met BioRender.</figcaption>
</figure>
</div>
<div class="therapy__pane therapy__pane--blue" role="tabpanel" id="pane-imm" aria-labelledby="tab-imm">
<div class="therapy__text"><p>Glutamineremmers kunnen de afweer tegen kanker versterken: L-DON en de variant JHU083 activeren T-cellen, en L-DON maakt alvleesklierkanker beter bereikbaar voor T-cellen.</p><p>Maar glutamineremming kan ook het eiwit PD-L1 op de tumor verhogen, dat T-cellen afremt. Een checkpointremmer (anti-PD-L1) schermt dat eiwit af. Samen werkten ze sterker dan elk middel apart.</p></div>
<figure class="chapter__figure">
  <a href="{{ '/assets/img/projects/bachelor_immuuntherapie.svg' | relative_url }}"><img src="{{ '/assets/img/projects/bachelor_immuuntherapie.svg' | relative_url }}" alt="Twee panelen: links remt PD-L1 op de tumorcel de T-cel; rechts schermt een antilichaam PD-L1 af en valt de T-cel de tumorcel aan" loading="lazy"></a>
  <figcaption>Links: na glutamineremming remt PD-L1 de T-cel. Rechts: met anti-PD-L1 valt de T-cel de tumorcel aan. Eigen figuur.</figcaption>
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
<p class="chapter__conclusion"><strong>Conclusie:</strong> alleen het glutaminemetabolisme remmen is niet genoeg. De toekomst ligt in combinaties die meerdere routes tegelijk aanpakken, zodat de kankercel geen uitweg meer heeft.</p>
  </div>
</section>
