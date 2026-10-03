---
layout: project
lang: nl
ref: bachelor-thesis
project: bachelor-thesis
section: bachelor
title: "Bachelorscriptie: combinatietherapieën met glutaminemetabolismeremmers"
lead: "Welke medicijncombinaties doorbreken de resistentie van kankercellen tegen glutaminemetabolismeremmers?"
description: Literatuurstudie naar combinatietherapieën die de resistentie van kankercellen tegen glutaminemetabolismeremmers kunnen doorbreken.
abstract: "Veel tumoren draaien op het aminozuur glutamine, maar medicijnen die dat blokkeren verliezen hun werking zodra kankercellen een omweg vinden. In deze literatuurstudie bracht ik die omwegen in kaart en welke combinaties ze kunnen afsluiten: een glutamineremmer samen met andere remmers, met bestraling of met immuuntherapie."
abstract_image: /assets/img/projects/bachelor_abstract.svg
abstract_alt: "Visuele samenvatting in drie stappen: een tumorcel draait op glutamine; met één remmer neemt de cel een omweg via glucose en vetzuren; een combinatietherapie remt alle routes en zet daarnaast radiotherapie en T-cellen (immuuntherapie) in"
image: /assets/img/projects/bachelor_abstract.png
course: BSc Biomedische Wetenschappen, Universiteit Utrecht, 2023
team: Individuele literatuurstudie
tools: [Literatuuronderzoek, Kankermetabolisme, Immunotherapie, Wetenschappelijk schrijven]
---

<section class="slide slide--full chapter">
  <div class="slide__text">
    <p class="slide__num"><span class="slide__kicker">Glutamine en kanker</span></p>
    <h2>Tumoren draaien op glutamine</h2>
  </div>
  <div class="chapter__body">
<div class="chapter__text">
<p>Kankercellen delen snel en hebben daarvoor veel energie en bouwstoffen nodig. Lang dacht men vooral aan suiker (glucose), maar veel tumoren blijken minstens zo afhankelijk van het aminozuur <strong>glutamine</strong>, dat ze in grote hoeveelheden uit het bloed opnemen via de transporter SLC1A5.</p>
<p>In de cel zet het enzym <strong>glutaminase (GLS)</strong> glutamine om in glutamaat. Dat is de brandstof voor de energiecentrale van de cel, en ook de grondstof voor:</p>
<ul class="chapter__list">
<li><strong>Bouwstoffen</strong> voor het DNA, de eiwitten en de celwand van nieuwe cellen.</li>
<li><strong>Bescherming:</strong> een antioxidant die schadelijke stoffen in de cel wegvangt.</li>
<li><strong>Een groeisignaal</strong> dat de cel aanzet tot groeien.</li>
</ul>
</div>
<figure class="chapter__figure chapter__figure--wide">
  <a href="{{ '/assets/img/projects/bachelor_glutamine_rollen.svg' | relative_url }}"><img src="{{ '/assets/img/projects/bachelor_glutamine_rollen.svg' | relative_url }}" alt="Schema van een kankercel: glutamine uit het bloed wordt door een enzym omgezet in brandstof voor energie, en levert ook bouwstoffen, bescherming en een groeisignaal" loading="lazy"></a>
  <figcaption>Wat glutamine doet in een kankercel. Alles loopt via glutaminase, de stap die de remmer CB-839 blokkeert. Eigen figuur.</figcaption>
</figure>
  </div>
</section>

<section class="slide slide--full chapter">
  <div class="slide__text">
    <p class="slide__num"><span class="slide__kicker">Resistentie</span></p>
    <h2>De kankercel neemt een omweg</h2>
  </div>
  <div class="chapter__body">
<p class="chapter__note chapter__note--problem">Bekende kankergenen voeren het glutaminegebruik nog verder op. Daarom zijn er remmers van glutaminase ontwikkeld. <strong>CB-839</strong> is als enige al bij patiënten getest, maar werkte als losse behandeling teleurstellend.</p>
<p class="chapter__lead">Hoe kan dat? Glutamine remmen remt de groei, maar doodt de kankercel vaak niet. De cel schakelt over op andere bronnen en houdt zo zijn energie en bouwstoffen op peil. In de literatuur vond ik vijf van zulke omwegen.</p>
<div class="hotfig" data-hotfig>
<div class="hotfig__stage">
<figure class="chapter__figure">
  <a href="{{ '/assets/img/projects/bachelor_omwegen.svg' | relative_url }}"><img src="{{ '/assets/img/projects/bachelor_omwegen.svg' | relative_url }}" alt="Schema van een kankercel waarin glutamine is geblokkeerd, terwijl glucose, vetzuren, een andere weg naar glutamaat, recyclen en andere aminozuren de energie op peil houden" loading="lazy"></a>
  <figcaption>Glutamine is geblokkeerd, maar via vijf omwegen blijft de cel energie houden. Eigen figuur.</figcaption>
</figure>
<button type="button" class="hotfig__spot" data-target="r0-nl" style="left:2%;top:38%;width:20%;height:19%" aria-label="Glutamine, geremd"></button><button type="button" class="hotfig__spot" data-target="r1-nl" style="left:8%;top:5%;width:21%;height:18%" aria-label="Omweg 1: suiker"></button><button type="button" class="hotfig__spot" data-target="r2-nl" style="left:69%;top:5%;width:23%;height:18%" aria-label="Omweg 2: vet"></button><button type="button" class="hotfig__spot" data-target="r3-nl" style="left:7%;top:82%;width:30%;height:16%" aria-label="Omweg 3: glutamaat"></button><button type="button" class="hotfig__spot" data-target="r4-nl" style="left:39%;top:64%;width:22%;height:23%" aria-label="Omweg 4: recyclen"></button><button type="button" class="hotfig__spot" data-target="r5-nl" style="left:71%;top:82%;width:23%;height:16%" aria-label="Omweg 5: aminozuren"></button>
</div>
<p class="hotfig__info" aria-live="polite" data-default="Beweeg over een route in de figuur, of tik erop, voor de uitleg.">Beweeg over een route in de figuur, of tik erop, voor de uitleg.</p>
<ol class="routes hotfig__list"><li id="r0-nl" class="routes__item routes__item--grey"><strong>Glutamine is geremd.</strong> CB-839 blokkeert glutaminase, dus glutamine levert geen brandstof meer. Toch blijft de cel energie houden, via de omwegen hieronder.</li><li id="r1-nl" class="routes__item routes__item--pink"><strong>1. Suiker in plaats van glutamine.</strong> Via de glycolyse stookt de cel meer glucose. In muizen bleef de cel draaien zonder glutamine; pas toen ook het suikergebruik werd geblokkeerd, kreeg bijna 40% van de muizen geen tumor.</li><li id="r2-nl" class="routes__item routes__item--green"><strong>2. Vet verbranden.</strong> Tumoren die ongevoelig werden voor CB-839, verbrandden meer vetzuren via het enzym CPT1.</li><li id="r3-nl" class="routes__item routes__item--purple"><strong>3. Een andere weg naar glutamaat.</strong> De cel maakt de volgende stap uit glutamine (glutamaat) via de glutaminase II-route of uit de stof NAAG.</li><li id="r4-nl" class="routes__item routes__item--grey"><strong>4. Eigen onderdelen recyclen (autofagie).</strong> De cel breekt eigen onderdelen af om bouwstoffen terug te winnen. Glutamine remmen kan dat juist aanzetten.</li><li id="r5-nl" class="routes__item routes__item--blue"><strong>5. Andere aminozuren opnemen.</strong> Extra transporters halen de aminozuren aspartaat en arginine binnen.</li></ol>
</div>
<script>
(function () {
  document.querySelectorAll('[data-hotfig]').forEach(function (box) {
    var info = box.querySelector('.hotfig__info');
    var spots = box.querySelectorAll('.hotfig__spot');
    function show(spot) {
      spots.forEach(function (s) { s.classList.toggle('is-active', s === spot); });
      var item = document.getElementById(spot.getAttribute('data-target'));
      info.innerHTML = item ? item.innerHTML : info.getAttribute('data-default');
      info.className = 'hotfig__info is-filled ' + (item ? item.className.replace('routes__item', 'hotfig__info') : '');
    }
    spots.forEach(function (s) {
      s.addEventListener('mouseenter', function () { show(s); });
      s.addEventListener('focus', function () { show(s); });
      s.addEventListener('click', function () { show(s); });
    });
    box.classList.add('is-ready');
  });
})();
</script>
  </div>
</section>

<section class="slide slide--full chapter">
  <div class="slide__text">
    <p class="slide__num"><span class="slide__kicker">Combinatietherapieën</span></p>
    <h2>De omwegen afsluiten</h2>
  </div>
  <div class="chapter__body">
<p class="chapter__lead">Omdat een kankercel zoveel uitwegen heeft, ligt de oplossing in combinaties: een glutamineremmer samen met één partner die een uitweg dichtzet of een zwakke plek benut. Ik vergeleek drie van zulke combinaties. Het zijn alternatieven, geen behandeling met alle drie tegelijk.</p>
<p class="therapy__intro"><strong>Glutamineremmer + één partner.</strong> <span>Beweeg over een therapie of tik erop voor de uitleg en het plaatje.</span></p>
<div class="therapy" data-therapy>
<div class="therapy__tabs" role="tablist">
<button type="button" class="therapy__tab therapy__tab--red is-active" role="tab" id="tab-met" aria-controls="pane-met" aria-selected="true"><span class="therapy__plus">+</span><span><strong>Andere remmers</strong><small>suiker, vet en glutamaat dicht</small></span></button>
<button type="button" class="therapy__tab therapy__tab--purple" role="tab" id="tab-rad" aria-controls="pane-rad" aria-selected="false"><span class="therapy__plus">+</span><span><strong>Bestraling</strong><small>geen schild, meer schade</small></span></button>
<button type="button" class="therapy__tab therapy__tab--blue" role="tab" id="tab-imm" aria-controls="pane-imm" aria-selected="false"><span class="therapy__plus">+</span><span><strong>Immuuntherapie</strong><small>T-cellen weer aan het werk</small></span></button>
</div>
<div class="therapy__pane therapy__pane--red is-active" role="tabpanel" id="pane-met" aria-labelledby="tab-met">
<div class="therapy__text"><p>Remmers die ook de andere brandstofroutes blokkeren: het gebruik van suiker, het verbranden van vet en de andere weg naar glutamaat. Zonder omwegen valt de motor stil. In diermodellen remden zulke combinaties de tumorgroei sterker dan elk middel apart.</p><p class="therapy__note">Niet alles hield stand: één combinatie die in het lab werkte, voegde bij patiënten met nierkanker niets toe.</p></div>
<figure class="chapter__figure">
  <a href="{{ '/assets/img/projects/bachelor_metabole_remmers.svg' | relative_url }}"><img src="{{ '/assets/img/projects/bachelor_metabole_remmers.svg' | relative_url }}" alt="Schema van een kankercel waarin glutamine, glucose, vetzuren en de andere weg naar glutamaat allemaal zijn geblokkeerd, zodat de energie uitvalt" loading="lazy"></a>
  <figcaption>Glutamine én de omwegen geblokkeerd: de cel heeft geen brandstof meer. Eigen figuur.</figcaption>
</figure>
</div>
<div class="therapy__pane therapy__pane--purple" role="tabpanel" id="pane-rad" aria-labelledby="tab-rad">
<div class="therapy__text"><p>Glutamine levert de grondstof voor een antioxidant: het schild waarmee de tumor zich beschermt tegen schadelijke stoffen. Tumoren die dat schild hard nodig hebben, zijn het gevoeligst voor de remmer.</p><p>Valt het schild weg, dan komt bestraling harder aan. In studies bij long- en hoofd-halskanker werkte de combinatie beter dan elk van beide apart.</p></div>
<figure class="chapter__figure">
  <a href="{{ '/assets/img/projects/bachelor_radiotherapie.svg' | relative_url }}"><img src="{{ '/assets/img/projects/bachelor_radiotherapie.svg' | relative_url }}" alt="Twee panelen: links beschermt een schild uit glutamine de tumorcel tegen schadelijke stoffen; rechts is glutamine geremd, valt het schild weg en beschadigt bestraling de cel" loading="lazy"></a>
  <figcaption>Links: glutamine levert het schild. Rechts: zonder schild maakt bestraling de cel kapot. Eigen figuur.</figcaption>
</figure>
</div>
<div class="therapy__pane therapy__pane--blue" role="tabpanel" id="pane-imm" aria-labelledby="tab-imm">
<div class="therapy__text"><p>Glutamine remmen kan het afweersysteem helpen: afweercellen (T-cellen) worden actiever en bereiken de tumor beter.</p><p>Maar de tumor reageert door meer rem-eiwitten op zijn oppervlak te zetten, die T-cellen afremmen. Een immuuntherapie die die rem blokkeert, lost dat op. Samen werkten ze sterker dan elk middel apart.</p></div>
<figure class="chapter__figure">
  <a href="{{ '/assets/img/projects/bachelor_immuuntherapie.svg' | relative_url }}"><img src="{{ '/assets/img/projects/bachelor_immuuntherapie.svg' | relative_url }}" alt="Twee panelen: links remmen rem-eiwitten op de tumorcel de T-cel; rechts blokkeert een medicijn de rem en valt de T-cel de tumorcel aan" loading="lazy"></a>
  <figcaption>Links: rem-eiwitten houden de T-cel tegen. Rechts: een medicijn blokkeert de rem en de T-cel valt aan. Eigen figuur.</figcaption>
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
<p class="chapter__conclusion"><strong>Conclusie:</strong> alleen glutamine remmen is niet genoeg. De toekomst ligt in combinaties die meerdere routes tegelijk aanpakken, zodat de kankercel geen uitweg meer heeft.</p>
  </div>
</section>
