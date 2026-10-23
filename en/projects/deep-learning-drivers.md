---
layout: project
lang: en
ref: deeplearning
project: deeplearning
section: master
title: Detecting distracted drivers with deep learning
lead: "Can a neural network tell from a camera image what state a driver is in?"
description: A custom convolutional neural network (CNN) that recognises six driver states with 95% accuracy, compared with a baseline CNN and transfer learning with DenseNet121.
image: /assets/img/projects/deeplearning_nauwkeurigheid_vergelijking_en.png
abstract: "A custom convolutional neural network (CNN) recognises six driver states from a single camera image, such as distracted or sleepy. Hyperparameter tuning and regularisation raised the accuracy from 79% to 95%, well above transfer learning with the pretrained DenseNet121."
abstract_image: /assets/img/projects/deeplearning_abstract_en.svg
abstract_alt: "Visual summary: a camera image of a driver with a phone passes a custom CNN, which recognises 'distracted'; 95% accuracy, baseline CNN 79%"
course: Deep Learning, spring 2025
team: Six students (group 6) · I built the best model
tools: [Python, TensorFlow/Keras, CNN, Optuna, Transfer learning, DenseNet121]
stats:
  - value: "95%"
    label: "accuracy on the test images (baseline CNN: 79%)"
  - value: "92%"
    label: "average recall per driver state (baseline CNN: 65%)"
  - value: "6"
    label: "driver states recognised"
models:
  - name: "Baseline CNN"
    tag: "starting point"
    text: "Three convolutional layers. Reached 79%, but overfitted on the training images."
  - name: "Custom CNN"
    tag: "own design"
    own: true
    text: "Four convolutional layers with more and more filters, plus regularisation against overfitting."
  - name: "Transfer learning"
    tag: "DenseNet121"
    text: "A network pretrained on millions of photos, then fine-tuned for this task."
---

{% include slide.html kicker="Problem" title="Is the driver distracted?" text="Distraction and fatigue cause many accidents. Can a model tell from a single camera image?" src="/assets/img/projects/deeplearning_voorbeeldbeelden.png" alt="Grid of example driver images, each with its label" photo=true %}

{% include slide.html kicker="Data" title="Almost 15,000 images, unevenly spread" text="Greyscale images of 72 × 128 pixels in six classes. Drinking and yawning are rare." src="/assets/img/projects/deeplearning_klassen_en.png" alt="Bar chart: safe driving 6,180 images, dangerous driving 4,642, distracted 2,080, sleepy 979, yawning 546 and drinking 428" %}

{% include models.html kicker="Models" title="Build or reuse?" text="A CNN learns by itself what to look for in an image, from edges to postures." %}

{% include slide.html kicker="Method" title="The architecture of my CNN" text="Each convolutional layer summarises the image into more and more feature maps. A final softmax layer picks one of the six states." src="/assets/img/projects/deeplearning_pipeline_en.svg" alt="Architecture: a camera image passes four convolutional layers with 32 to 256 filters and a softmax layer, which picks one of six states" full=true %}

{% include slide.html kicker="Results" title="From 79% to 95%" text="My CNN reaches 95% accuracy on the test images, versus 79% for the baseline CNN and 84% for transfer learning with DenseNet121. The average recall per state also rose sharply, from 65% to 92%, so the rare states are found much more often." src="/assets/img/projects/deeplearning_resultaat_en.svg" alt="Bar chart: baseline CNN 79%, DenseNet121 84%, my CNN 95% accuracy" full=true %}

{% include slide.html kicker="Evaluation" title="Strong, but not ready for the road" text="'Distracted' and 'safe driving' remain the hardest to tell apart. Real use also requires fairness between groups of drivers and privacy." statement=true %}

<div class="role" markdown="1">
## My role
I built the best model: the second round of hyperparameter tuning with Optuna, the regularisation against overfitting and the architecture with more filters per layer. I also ran the transfer-learning experiments with DenseNet121.
</div>
