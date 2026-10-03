# Portfolio Giada Kruidenier

Persoonlijke portfoliowebsite in het Nederlands en Engels, gebouwd met [Jekyll](https://jekyllrb.com/) zodat GitHub Pages hem zonder extra stappen kan publiceren.

Na publicatie staat de site op **https://gkruidenier.github.io/portfolio/** (Nederlands) en **/portfolio/en/** (Engels).

## Waar staat wat

| Map of bestand | Inhoud |
|---|---|
| `_config.yml` | Naam, e-mail, GitHub, LinkedIn en profielfoto |
| `_data/projects.yml` | Alle projecten: titel, korte samenvatting, kerncijfer en afbeelding voor de overzichtspagina's |
| `_data/i18n.yml` | Vaste teksten van menu en knoppen in beide talen |
| `index.html`, `en/index.html` | Homepagina (NL en EN) |
| `master/`, `bachelor/`, `persoonlijk/` (en `en/...`) | Overzichtspagina's |
| `projecten/*.md`, `en/projects/*.md` | Eén pagina per project, in gewone Markdown |
| `assets/img/projects/` | Grafieken en afbeeldingen |
| `assets/video/` | De scrollanimatie van Oosterslicht |
| `assets/css/style.css` | Vormgeving; kleuren staan bovenaan als variabelen |

## Veelvoorkomende aanpassingen

**Profielfoto toevoegen.** Zet de foto in `assets/img/` (bijvoorbeeld `profiel.jpg`, vierkant werkt het best) en vul in `_config.yml` in: `photo: "/assets/img/profiel.jpg"`.

**LinkedIn toevoegen.** Vul in `_config.yml` je profiel-URL in bij `linkedin:`. De knoppen verschijnen dan vanzelf.

**Een project toevoegen (bijvoorbeeld jobscout-ai).**
1. Haal in `_data/projects.yml` de regel `status: coming-soon` weg bij het project en vul `url`, `summary` en eventueel `image` in, voor `nl` en `en`.
2. Kopieer een bestaande projectpagina, bijvoorbeeld `projecten/oosterslicht.md`, naar `projecten/jobscout-ai.md` en `en/projects/jobscout-ai.md`.
3. Pas bovenaan `ref`, `project` (gelijk aan het `id` in `projects.yml`) en `permalink` of bestandsnaam aan, en schrijf de tekst.

Een grafiek in een projectpagina zet je erin met:

```liquid
{% include figure.html src="/assets/img/projects/mijn_grafiek.png" alt="Wat er te zien is" caption="Onderschrift" %}
```

## Lokaal bekijken

```bash
gem install jekyll
jekyll serve
```

Open daarna http://localhost:4000/portfolio/.
