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
models:
  - name: "Baseline CNN"
    tag: "starting point"
    text: "A small network with three layers of 8 filters each. Reached 79%, but memorised the training data too much."
  - name: "Custom CNN"
    tag: "best model"
    own: true
    text: "Four layers where the number of filters doubles per layer (32 to 256), with batch normalisation and dropout against overfitting."
  - name: "DenseNet121"
    tag: "transfer learning"
    text: "A network already trained on millions of photos, with custom layers on top for these six classes."
---

{% include slide.html kicker="Problem" title="Can a camera tell how the driver is doing?" text="Distraction and fatigue behind the wheel cause many accidents. In-car systems can warn drivers, but only if a model can tell from one camera image whether someone is driving safely, distracted, drinking, sleepy or yawning." src="/assets/img/projects/deeplearning_voorbeeldbeelden.png" alt="Grid of example driver images, each with its label" photo=true %}

{% include slide.html kicker="Data" title="Six classes, unevenly distributed" text="Greyscale images of 72 × 128 pixels from the Kaggle dataset *Driver Inattention Detection*. Drinking and yawning are much rarer than safe driving." src="/assets/img/projects/deeplearning_klassenverdeling.png" alt="Bar chart of the number of images per class" %}

{% include models.html kicker="Models" title="Build or reuse?" text="A convolutional neural network (CNN) learns to recognise patterns in images by itself, from edges to postures. We compared a custom CNN with a pretrained network." %}

{% include slide.html kicker="Method" title="Step by step from 79% to 95%" text="Every change was tested separately on a validation set; only what helped was kept. The test set was used only at the end." src="/assets/img/projects/deeplearning_methode_en.svg" alt="Six-step method diagram: data, baseline, preprocessing, tuning, architecture and evaluation" full=true %}

{% include slide.html kicker="Results" title="The custom CNN wins clearly" text="95% accuracy on the test set, versus 79% for the baseline and 84% for DenseNet121. Average recall rose from 0.65 to 0.92." src="/assets/img/projects/deeplearning_nauwkeurigheid_vergelijking_en.png" alt="Bar chart of test accuracy: baseline 79%, DenseNet121 84%, custom CNN 95%" %}

{% include slide.html kicker="Results" title="Learns without overfitting" text="Training and validation stay close together. Per class, the AUC lies between 0.97 and 1.00." src="/assets/img/projects/deeplearning_leercurve_beste_model.png" alt="Line chart of training and validation accuracy per epoch" src2="/assets/img/projects/deeplearning_roc_beste_model.png" alt2="ROC curves per class with AUC between 0.97 and 1.00" full=true %}

{% include slide.html kicker="Evaluation" title="Strong, but not ready for the road" text="'Distracted' and 'safe driving' remain the hardest pair. Colour images and higher resolution could help. Real use also requires attention to bias between groups of drivers, privacy and security." statement=true %}

<div class="role" markdown="1">
## My role
I built the best model: the second Optuna round, the choice for dropout and the doubling-filter architecture. I also prepared the images and ran the DenseNet121 experiments.
</div>
