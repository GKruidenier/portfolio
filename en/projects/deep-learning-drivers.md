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
abstract: "A custom convolutional neural network recognises six driver states from in-car camera images, from safe driving to yawning. With Optuna tuning, more dropout and an architecture with doubling filters, accuracy rose from 79% to 95%, well above transfer learning with DenseNet121."
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
---

{% include slide.html title="Six states behind the wheel" text="Greyscale images of 72 × 128 pixels: safe, dangerous, distracted, drinking, sleepy and yawning." src="/assets/img/projects/deeplearning_voorbeeldbeelden.png" alt="Grid of example driver images, each with its label" photo=true %}

{% include slide.html title="Unevenly distributed" text="Drinking and yawning are much rarer than safe driving. Class weights and augmentation did not help." src="/assets/img/projects/deeplearning_klassenverdeling.png" alt="Bar chart of the number of images per class" %}

{% include slide.html title="From 79% to 95%" text="My own CNN beats the baseline and the pretrained DenseNet121 (84%). Average recall rose from 0.65 to 0.92." src="/assets/img/projects/deeplearning_nauwkeurigheid_vergelijking_en.png" alt="Bar chart of test accuracy: baseline 79%, DenseNet121 84%, custom CNN 95%" %}

{% include slide.html title="Learns without overfitting" text="Training and validation stay close together. Per class, the AUC lies between 0.97 and 1.00." src="/assets/img/projects/deeplearning_leercurve_beste_model.png" alt="Line chart of training and validation accuracy per epoch" src2="/assets/img/projects/deeplearning_roc_beste_model.png" alt2="ROC curves per class with AUC between 0.97 and 1.00" full=true %}

<div class="role" markdown="1">
## My role
I built the best model: the second Optuna round, the choice for dropout and the doubling-filter architecture. I also ran the DenseNet121 experiments.
</div>
