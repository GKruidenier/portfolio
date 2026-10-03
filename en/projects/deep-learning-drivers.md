---
layout: project
lang: en
ref: deeplearning
project: deeplearning
section: master
title: Detecting distracted drivers with deep learning
lead: "Can a neural network tell from a camera image what state a driver is in?"
description: A custom CNN that recognises six driver states with 95% accuracy, compared with a baseline and transfer learning (DenseNet121).
image: /assets/img/projects/deeplearning_nauwkeurigheid_vergelijking_en.png
abstract: "A custom convolutional neural network recognises six driver states from a single camera image. Targeted tuning raised accuracy from 79% to 95%, well above a pretrained network."
abstract_image: /assets/img/projects/deeplearning_abstract_en.svg
abstract_alt: "Visual summary: a camera image of a driver with a phone passes a custom neural network, which recognises 'distracted'; 95% of images correct, first model 79%"
course: Deep Learning, spring 2025
team: Six students (group 6) · I built the best model
tools: [Python, TensorFlow/Keras, CNN, Optuna, Transfer learning, DenseNet121]
stats:
  - value: "95%"
    label: accuracy on the test set (baseline 79%)
  - value: "0.92"
    label: average recall (baseline 0.65)
  - value: "6"
    label: driver states recognised
models:
  - name: "Simple network"
    tag: "starting point"
    text: "Three layers. Reached 79%, but memorised the training images too much."
  - name: "My network"
    tag: "own design"
    own: true
    text: "Four layers that learn more and more features, with measures against memorising."
  - name: "Pretrained network"
    tag: "DenseNet121"
    text: "Already trained on millions of photos, then adapted to this task."
---

{% include slide.html kicker="Problem" title="Is the driver distracted?" text="Distraction and fatigue cause many accidents. Can a model tell from a single camera image?" src="/assets/img/projects/deeplearning_voorbeeldbeelden.png" alt="Grid of example driver images, each with its label" photo=true %}

{% include slide.html kicker="Data" title="Almost 15,000 images, unevenly spread" text="Greyscale images of 72 × 128 pixels in six classes. Drinking and yawning are rare." src="/assets/img/projects/deeplearning_klassen_en.png" alt="Bar chart: safe driving 6,180 images, dangerous driving 4,642, distracted 2,080, sleepy 979, yawning 546 and drinking 428" %}

{% include models.html kicker="Models" title="Build or reuse?" text="A neural network for images learns by itself what to look for, from edges to postures." %}

{% include slide.html kicker="Method" title="How the network looks" text="Each layer summarises the image into more and more features. The last layer picks one of the six states." src="/assets/img/projects/deeplearning_pipeline_en.svg" alt="Pipeline: a camera image passes four layers with more and more features and a decision layer, which picks one of six states" full=true %}

{% include slide.html kicker="Results" title="From 79% to 95%" text="My network recognises 95% of the test images correctly, versus 79% for the first network and 84% for the pretrained network. The rare states are also found much more often (from 65% to 92%)." src="/assets/img/projects/deeplearning_resultaat_en.svg" alt="Bar chart: first network 79%, pretrained network 84%, my network 95% correct" full=true %}

{% include slide.html kicker="Evaluation" title="Strong, but not ready for the road" text="'Distracted' and 'safe driving' remain the hardest to tell apart. Real use also requires fairness between groups of drivers and privacy." statement=true %}

<div class="role" markdown="1">
## My role
I built the best model: the second round of automatic tuning, the choice for dropout and the design with more features per layer. I also ran the experiments with the pretrained network.
</div>
