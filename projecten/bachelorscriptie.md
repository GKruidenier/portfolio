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
<p class="chapter__lead">Omdat een kankercel zoveel uitwegen heeft, ligt de oplossing in combinaties: een glutaminaseremmer samen met een partner die precies die uitweg dichtzet of een zwakke plek benut. Ik vergeleek drie soorten partners.</p>
<figure class="chapter__figure chapter__figure--wide">
  <a href="{{ '/assets/img/projects/bachelor_combinaties.svg' | relative_url }}"><img src="{{ '/assets/img/projects/bachelor_combinaties.svg' | relative_url }}" alt="Overzicht: een glutaminaseremmer in het midden, gecombineerd met metabole remmers, radiotherapie of immuuntherapie" loading="lazy"></a>
  <figcaption>De drie soorten combinaties die ik vergeleek. Eigen figuur.</figcaption>
</figure>
<div class="partners">
<div class="partner partner--red"><h3>Metabole remmers</h3><p>Blokkeren de omwegen zelf: metformine of Glutor remmen het glucosegebruik, MLN128 en everolimus remmen mTOR, etomoxir remt de vetzuurverbranding en 2-PMPA de aanmaak van glutamaat uit NAAG. In diermodellen remden zulke combinaties de tumorgroei sterker dan elk middel apart.</p><p class="partner__note">Kanttekening: cabozantinib werkte in het lab, maar voegde in een eerste klinische studie bij nierkanker niets toe.</p></div>
<div class="partner partner--purple"><h3>Radiotherapie</h3><p>Hoge oxidatieve stress voorspelt beter dan het glutaminegebruik of een tumor gevoelig is. Tumoren met een overactieve NRF2-beschermingsroute, bijvoorbeeld door KEAP1-, KRAS- of IDH-mutaties, zijn daarom goede kandidaten. Een glutaminaseremmer verlaagt het glutathion, zodat bestraling harder aankomt: longkankercellen werden gevoeliger voor radiotherapie en bij hoofd-halskanker gaf CB-839 plus bestraling een sterkere respons.</p></div>
<div class="partner partner--blue"><h3>Immuuntherapie</h3><p>Glutamineremmers kunnen de afweer tegen kanker versterken: L-DON en de variant JHU083 activeren T-cellen, en L-DON maakt alvleesklierkanker beter bereikbaar voor T-cellen. Tegelijk kan glutamineremming het remmende eiwit PD-L1 op de tumor verhogen. Juist daarom werkt de combinatie met een checkpointremmer (anti-PD-L1) sterker dan elk middel apart.</p></div>
</div>
<div class="chapter__cols chapter__cols--figs">
<figure class="chapter__figure">
  <a href="{{ '/assets/img/projects/bachelor_combinatietherapie.png' | relative_url }}"><img src="{{ '/assets/img/projects/bachelor_combinatietherapie.png' | relative_url }}" alt="Schema van een kankercel met de aangrijpingspunten van metabole remmers naast glutaminaseremmers" loading="lazy"></a>
  <figcaption>Metabole remmers die in combinatie met glutaminaseremmers werkten. Figuur uit mijn scriptie.</figcaption>
</figure>
<figure class="chapter__figure">
  <a href="{{ '/assets/img/projects/bachelor_oxidatieve_stress.png' | relative_url }}"><img src="{{ '/assets/img/projects/bachelor_oxidatieve_stress.png' | relative_url }}" alt="Schema van de factoren die oxidatieve stress verhogen, zoals radiotherapie, KRAS- en IDH-mutaties, en de NRF2-route die de cel beschermt" loading="lazy"></a>
  <figcaption>Hoge NRF2-activiteit als teken van glutamine-afhankelijkheid; radiotherapie verhoogt de oxidatieve stress. Figuur uit mijn scriptie, gemaakt met BioRender.</figcaption>
</figure>
</div>
<p class="chapter__conclusion"><strong>Conclusie:</strong> alleen het glutaminemetabolisme remmen is niet genoeg. De toekomst ligt in combinaties die meerdere routes tegelijk aanpakken, zodat de kankercel geen uitweg meer heeft.</p>
  </div>
</section>
