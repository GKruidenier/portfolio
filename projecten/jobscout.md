---
layout: project
lang: nl
ref: jobscout
project: jobscout
section: personal
title: "jobscout-ai: een AI-agent die vacatures zoekt"
lead: "Je maakt een eigen profiel met een chat, en daarna zoekt de app vacatures die bij jou passen. Het project staat nog in een vroeg stadium."
description: Een persoonlijk project in een vroeg stadium. Je maakt een profiel met een chat, een agent zoekt passende vacatures en leert van je feedback.
image: /assets/img/projects/jobscout_poster.png
abstract: "Vacatures zoeken makkelijker maken. De app zoekt werk dat echt op jou is afgestemd, zodat je niet door hopen vacatures hoeft te waden en je motivatie verliest. Zo houd je meer tijd over voor wat echt belangrijk is, en vind je ook vacatures die je zelf misschien nooit had gevonden. De screenshots komen uit een demostand met een verzonnen profiel en verzonnen werkgevers."
course: Persoonlijk project, 2026, in ontwikkeling
team: Alleen ik
tools: [Python, LangGraph, FastAPI, Next.js, Large Language Models (LLM)]
---

{% include slide.html
  title="Een eigen profiel, met een chat"
  text="Een chatbot vraagt naar je opleiding, je ervaring, wat voor werk je zoekt en wat je belangrijk vindt. Rechts groeit je profiel mee, en daarna verbeteren jij en de AI het samen."
  src="/assets/img/projects/jobscout_gesprek.png"
  alt="Het begingesprek: links de chat met keuzeknoppen om te kiezen wat je belangrijk vindt, rechts het profiel dat zich vult met de antwoorden"
  full=true %}

{% include slide.html
  title="Elke dag passende vacatures"
  text="Het idee is dat een agent elke dag zoekt op de eigen sites van werkgevers. Bij elke vacature staat waarom hij past, met een citaat uit de tekst en een bron."
  src="/assets/img/projects/jobscout_vacatures.png"
  alt="Twee gevonden vacatures met werkgever, plaats, ervaringsniveau, citaat, bron en de controle dat de vacature nog open staat"
  full=true %}

{% include slide.html
  title="Je feedback maakt het zoeken beter"
  text="Bij elke vacature geef je aan of hij past, en waarom niet. De app verwerkt die feedback in een nieuwe versie van je profiel, die pas telt als jij hem goedkeurt."
  src="/assets/img/projects/jobscout_feedback.png"
  alt="Een vacature met de feedback 'past niet' en de reden 'sector spreekt me niet aan', met bovenaan de knop Verwerk in mijn profiel"
  full=true %}
