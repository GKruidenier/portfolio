---
layout: project
lang: en
ref: deeplearning
project: deeplearning
section: master
title: Detecting distracted drivers with deep learning
lead: Can a neural network tell from an in-car camera image what state a driver is in? That is the basis of systems that warn drivers about fatigue or distraction.
description: A custom CNN that recognises six driver states with 95% accuracy, compared with a baseline and transfer learning (DenseNet121).
image: /assets/img/projects/deeplearning_nauwkeurigheid_vergelijking_en.png
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

## The question

Can a neural network tell from an in-car camera image what state a driver is in? That is the basis of systems that warn drivers about fatigue or distraction.

## The data

The *Driver Inattention Detection* dataset from Kaggle: greyscale images of drivers (downscaled to 72 × 128 pixels) in six classes: safe driving, dangerous driving, distracted, drinking, sleepy and yawning. The classes are very unbalanced; drinking and yawning are much rarer than safe driving.

{% include figure.html src="/assets/img/projects/deeplearning_voorbeeldbeelden.png" alt="Grid of example driver images, each with its label" caption="Example images from the dataset with their labels." photo=true %}

{% include figure.html src="/assets/img/projects/deeplearning_klassenverdeling.png" alt="Bar chart of the number of images per class" caption="The classes are very unbalanced." %}

## Approach

- **Baseline.** A simple CNN with three convolutional layers reached 79% on the test set, but overfitted and mostly confused "distracted" with "safe driving".
- **Preprocessing tested.** Class weights and data augmentation made the model worse, so they were not used.
- **Hyperparameter tuning with Optuna.** A search over the number of filters, kernel size, dense units, learning rate, optimiser and activation function, then refined with a second search around the best settings.
- **Improved architecture.** L2 regularisation did not help; more dropout did. The breakthrough was a network in which the number of filters doubles at each layer (starting at 32): as max-pooling makes the image smaller, the network gets more channels to store features in.
- **Transfer learning.** A pre-trained DenseNet121 with custom classification layers and a learning-rate scheduler, as a comparison with our own model.

## Results

{% include figure.html src="/assets/img/projects/deeplearning_nauwkeurigheid_vergelijking_en.png" alt="Bar chart of test accuracy: baseline 79%, DenseNet121 84%, custom CNN 95%" caption="Baseline, transfer learning and the custom model compared on the test set." %}

- **The optimised custom CNN reaches 95% accuracy on the test set**, against 79% for the baseline. Average recall rose from 0.65 to 0.92.
- The pre-trained DenseNet121 stalled at 84%: its pre-trained features suited these small greyscale images less well.
- "Distracted" and "safe driving" remain the hardest pair, but the number of mistakes between them dropped sharply.
- The report also covers the ethical side: bias in the training data, privacy of in-car camera monitoring and vulnerability to manipulation.

{% include figure.html src="/assets/img/projects/deeplearning_leercurve_beste_model.png" alt="Line chart of training and validation accuracy per epoch" caption="Training and validation accuracy of the best model: the two lines stay close, so there is little overfitting." %}

<div class="figure-pair">
{% include figure.html src="/assets/img/projects/deeplearning_confusionmatrix_beste_model.png" alt="Confusion matrix of the best model on the test set" caption="Confusion matrix on the test set." %}
{% include figure.html src="/assets/img/projects/deeplearning_roc_beste_model.png" alt="Per-class ROC curves with AUC between 0.97 and 1.00" caption="Per-class ROC curves: AUC between 0.97 and 1.00." %}
</div>

<div class="role" markdown="1">
## My role
I built the best-performing model: the second Optuna search, the choice of dropout over L2 regularisation and the architecture with doubling filters. I also preprocessed the images for the DenseNet121 transfer model and ran its experiments (including the learning-rate scheduler), and co-wrote the methods section.
</div>
