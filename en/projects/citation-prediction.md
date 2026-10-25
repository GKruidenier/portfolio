---
layout: project
lang: en
ref: citations
project: citations
section: master
title: Predicting how often a scientific paper will be cited
lead: "Can you predict how often a paper will be cited from its title, abstract, authors, venue and year?"
description: A natural language processing (NLP) pipeline with TF-IDF, Sentence-BERT and Ridge regression that predicts citation counts for 1.2 million papers. Top 5 of the Machine Learning course.
image: /assets/img/projects/citaties_mpl_abstract.png
abstract: |
  <div style="display:grid; grid-template-columns:repeat(auto-fit, minmax(230px, 1fr)); gap:18px 28px;">
  <div><h3 style="margin:0 0 6px;">The problem</h3><p style="margin:0; font-size:.95rem; line-height:1.5;">For almost 1.2 million scientific papers we got the title, abstract, authors, venue, year and references, plus the number of times each paper was cited. The task: predict that number for papers the model has not seen.</p></div>
  <div><h3 style="margin:0 0 6px;">My solution</h3><p style="margin:0; font-size:.95rem; line-height:1.5;">I turned the text into numbers with natural language processing (NLP): term frequency–inverse document frequency (TF-IDF) for words, author names and venues, and Sentence-BERT embeddings for the meaning of the title. A Ridge regression predicts the square root of the citation count, so the few extremely cited papers do not dominate.</p></div>
  <div><h3 style="margin:0 0 6px;">Result</h3><p style="margin:0; font-size:.95rem; line-height:1.5;">On the validation papers the mean absolute error (MAE) is 29.0 citations, against 33.8 when you always predict the median: 14% smaller. On the hidden test set of the course my model finished in the top 5 of the leaderboard.</p></div>
  </div>
# eerder: abstract_image: /assets/img/projects/citaties_abstract_en.svg  (concept-figuur, bestand blijft bewaard)
abstract_image: /assets/img/projects/citaties_mpl_abstract.png
abstract_alt: "Three panels. Left: share of papers per number of citations; 15% has 0 citations and 32% exactly 50. Middle: mean absolute error on the validation papers; always predicting the median 33.8, my Ridge model 29.0. Right: mean absolute error per group of actual citations for the median and my model."
course: Machine Learning, MSc Data Science and Society
team: "Individual project. My role: everything, from text preprocessing and feature engineering to model selection and one script that runs the whole pipeline."
tools: [Python, scikit-learn, NLTK, TF-IDF, Sentence-BERT, Ridge, LightGBM, Random Forest]
stats:
  - value: "Top 5"
    label: "on the course leaderboard (hidden test set)"
  - value: "29.0"
    label: "citations off on average for validation papers (median: 33.8)"
  - value: "1.2 million"
    label: "papers with title, abstract, authors, venue and year"
sample:
  caption: "What the data looks like"
  columns: ["Title", "Venue", "Year", "Citations"]
  rows:
    - ["Feature-based video mosaic", "international conference on image processing", "2000", "51"]
    - ["On linear prediction of Internet traffic for packet and burst switching networks", "international conference on computer communications and networks", "2001", "81"]
    - ["Iterative multiuser detection/decoding for turbo coded CDMA systems", "IEEE Communications Letters", "2001", "50"]
    - ["Inverse spectral problems for Sturm–Liouville operators with partial information", "Applied Mathematics Letters", "2013", "0"]
  note: "Plus abstract, authors and references per paper: 1,189,209 papers from 1950 to 2017, 3,873 venues and about one million different authors (2 GB)."
---

{% include data.html kicker="Data" title="1.2 million papers, one number to predict" text="Each paper comes with its title, abstract, authors, venue, year and a list of the papers it cites. The label is the number of citations (`n_citation`). I held back one third of the papers as a **validation set** (396,403 papers) to compare models on papers they had not seen; the other two thirds (792,806) were used for training." %}

{% include slide.html kicker="Data exploration" title="Most papers are rarely cited, a few very often" text="The citation counts are extremely skewed. The median is 22, but the mean is 38.6 because of a long tail: 5% of the papers have 100 citations or more, and the most cited one has 25,835. A model that minimises squared errors would chase those few outliers. Two other things stand out: 15% of the papers have no citations at all, and a striking 32% have **exactly 50**." src="/assets/img/projects/citaties_mpl_verdeling.png" alt="Left: bar chart of the share of papers per number of citations up to 150; 15% has 0 citations, then the share drops quickly, with a single spike of 32% at exactly 50. Median 22, mean 38.6, maximum 25,835. Right: on a log-log scale the share of papers with at least a given number of citations: 5% has 100 or more, 0.15% 1,000 or more and 0.0018% 10,000 or more." full=true %}

{% include slide.html kicker="Method · Features" title="From text to numbers" text="A model only works with numbers, so each part of a paper becomes a set of features. Titles and abstracts are cleaned with the Natural Language Toolkit (NLTK): stop words are removed and words are lemmatised (reduced to their dictionary form). **Term frequency–inverse document frequency (TF-IDF)** then gives each word a weight that is high when the word is frequent in this paper but rare across all papers. I used the same trick for full author names, venues and decades. **Sentence-BERT**, a language model built on Bidirectional Encoder Representations from Transformers (BERT), turns each title into 384 numbers that capture its meaning. The last feature is the average number of citations of the papers in the reference list.

**Ridge regression** is a linear regression with an L2 penalty that keeps the weights small, which matters with about two million features. It is trained on the **square root** of the citation count, and the prediction is squared back afterwards." src="/assets/img/projects/citaties_mpl_pipeline_en.svg" alt="Pipeline from input to prediction. Title, abstract, authors, venue, year and references per paper. Titles and abstracts are cleaned with NLTK and turned into TF-IDF features; the title also goes through Sentence-BERT (all-MiniLM-L6-v2) into an embedding of 384 numbers. Authors become TF-IDF over full names, venue and decade TF-IDF with one token each, year is standardised and the references become the mean citations of the cited papers. All features go into a Ridge regression with alpha 11, trained on the square root of the citations; the prediction squared gives the number of citations." full=true %}

{% include slide.html kicker="Results · Features" title="Who and where matter most" text="I compared dozens of feature combinations on the validation papers. The figure shows the main steps, each time with the same Ridge regression. The measure is the **mean absolute error (MAE)**: how many citations a prediction is off on average. Always predicting the median (22 citations) is off by 33.8 on average. Year and author words bring that down to 31.6, full author names and the abstract to 30.7, and venue and decade to 29.1. The citations of the references, the title words and the Sentence-BERT embedding each improve it only slightly, to 29.0 in the final model: 14% smaller than the median." src="/assets/img/projects/citaties_mpl_ladder.png" alt="Horizontal bar chart of the mean absolute error on the validation papers. Always predict the mean 34.75, always predict the median 33.75, year and author words 31.62, plus full author names and abstract 30.73, plus venue and decade 29.09, plus citations of references 29.08, plus title words 29.02, plus Sentence-BERT title 28.98 (final model)." full=true %}

{% include slide.html kicker="Results · Errors" title="Good at the bottom, weak in the tail" text="Where are the errors? For papers without citations my model is off by 13 on average, against 22 for the median, and for papers with 51–100 citations by 29 instead of 48. For the 5% of papers with more than 100 citations the error stays large (205): a linear model on the square root rarely predicts such high numbers. The papers with exactly 50 citations, a third of the data, are hardly predicted better than with the median (27 against 28)." src="/assets/img/projects/citaties_mpl_fout_per_groep.png" alt="Grouped bar chart on a log scale of the mean absolute error per group of actual citations, for always predicting the median (22) and my Ridge model. 0 citations (15% of papers): 22 and 13. 1–10 (27%): 18 and 15. 11–49 (15%): 8 and 16. Exactly 50 (32%): 28 and 27. 51–100 (6%): 48 and 29. More than 100 (5%): 252 and 205." full=true %}

{% include slide.html kicker="Discussion" title="A simple model on well-chosen features" text="The teachers held back the real citation counts of the test papers and ranked all predictions; my model finished in the top 5 of the course. The gain over the median comes mostly from who wrote the paper and where it appeared, not from the language model. A next step is a model that handles the long tail better, and a closer look at the peak at exactly 50 citations." %}
