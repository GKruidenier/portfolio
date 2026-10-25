---
layout: project
lang: en
ref: deeplearning
project: deeplearning
section: master
title: Classifying driver behaviour with deep learning
lead: "Can a neural network tell from a single camera image what state a driver is in?"
description: A custom convolutional neural network (CNN) that recognises six driver states with 95% accuracy, compared with a baseline CNN and transfer learning with DenseNet121.
image: /assets/img/projects/deeplearning_mpl_abstract.png
abstract: |
  <div style="display:grid; grid-template-columns:repeat(auto-fit, minmax(230px, 1fr)); gap:18px 28px;">
  <div><h3 style="margin:0 0 6px;">The problem</h3><p style="margin:0; font-size:.95rem; line-height:1.5;">Distraction and fatigue cause many traffic accidents. From almost 15,000 in-car camera images we had to classify the driver into one of six states, such as safe driving, distracted, drinking or yawning.</p></div>
  <div><h3 style="margin:0 0 6px;">Our solution</h3><p style="margin:0; font-size:.95rem; line-height:1.5;">We started from a small baseline convolutional neural network (CNN) and improved it step by step. I tuned the hyperparameters with Optuna and built a deeper CNN with more filters per layer, batch normalisation and dropout. We compared it with transfer learning on DenseNet121, a network pretrained on ImageNet.</p></div>
  <div><h3 style="margin:0 0 6px;">Result</h3><p style="margin:0; font-size:.95rem; line-height:1.5;">My CNN reaches 95% accuracy on the test images, against 79% for the baseline CNN and 84% for DenseNet121. The macro-averaged recall rose from 0.65 to 0.92, so the rare states are now found much more often. 'Distracted' and 'safe driving' remain the hardest to tell apart.</p></div>
  </div>
# eerder: abstract_image: /assets/img/projects/deeplearning_abstract_en.svg  (eigen figuur, bestand blijft bewaard)
abstract_image: /assets/img/projects/deeplearning_mpl_abstract.png
abstract_alt: "Three panels. Left: six example camera images from the dataset, labelled safe driving, dangerous driving, distracted and yawning. Middle: accuracy on the test set; baseline CNN 79%, DenseNet121 84%, my CNN 95%. Right: recall per driver state for the baseline CNN and my CNN; my CNN is higher for every state, most of all for yawning (0.19 to 1.00) and distracted (0.63 to 0.92)."
course: Deep Learning, spring 2025
team: "Six students (group 6). My role: the second round of hyperparameter tuning with Optuna and the final CNN architecture (best model), preparing the images for and running the DenseNet121 transfer-learning experiments, and co-writing the methodology section."
tools: [Python, TensorFlow/Keras, CNN, Optuna, Transfer learning, DenseNet121]
stats:
  - value: "95%"
    label: "accuracy on the test images (baseline CNN: 79%)"
  - value: "0.92"
    label: "macro-averaged recall over the six states (baseline CNN: 0.65)"
  - value: "14,855"
    label: "in-car camera images in six classes"
models:
  - name: "Baseline CNN"
    tag: "starting point"
    text: "Three small convolutional layers with 8 filters each, prescribed by the assignment."
  - name: "My CNN"
    tag: "own design"
    own: true
    text: "Four convolutional layers with 32 to 256 filters, batch normalisation and dropout."
  - name: "Transfer learning"
    tag: "DenseNet121"
    text: "A network pretrained on ImageNet. Its layers stay frozen; only new dense layers on top are trained."
---

{% include slide.html kicker="Problem" title="The assignment: who is paying attention?" text="Distraction and fatigue at the wheel cause many accidents. In this group assignment we used the [Driver Inattention Detection dataset](https://www.kaggle.com/datasets/zeyad1mashhour/driver-inattention-detection-dataset): in-car camera images, each labelled with one of six driver states. The assignment had four parts:" points="**Baseline:** build a given small CNN exactly as specified and evaluate it | **Improve:** tune at least six hyperparameters with a clear rationale and beat the baseline | **Transfer learning:** reuse a pretrained network (VGG16, ResNet50 or DenseNet121) with frozen layers and only new dense layers on top | **Discuss:** further improvements from the literature, and the risks of using such a system on the road, such as bias, privacy and security" src="/assets/img/projects/deeplearning_voorbeeldbeelden.png" alt="Fifteen example images from the dataset, each with its label: safe driving, dangerous driving (phone at the ear), distracted and yawning." photo=true full=true %}

{% include slide.html kicker="Data exploration" title="Almost 15,000 noisy greyscale images" text="Each image is a frame from an in-car camera, scaled down to 72 × 128 pixels in greyscale, with random noise added by the preprocessing code of the assignment, which we were not allowed to change. The six states are very unevenly spread: safe driving makes up 42% of the images, drinking and yawning only 3–4%. The images come in a fixed split of 11,948 training, 1,922 validation and 985 test images." src="/assets/img/projects/deeplearning_mpl_klassen.png" alt="Horizontal bar chart of the number of images per driver state: safe driving 6,180 (42%), dangerous driving 4,642 (31%), distracted 2,080 (14%), sleepy driving 979 (7%), yawning 546 (4%) and drinking 428 (3%); 14,855 images in total." full=true %}

{% include slide.html kicker="Method · Baseline" title="Start: the prescribed baseline CNN" text="The assignment prescribed the baseline exactly: three blocks of a convolutional layer (8 filters of 3 × 3) and max pooling, then a dense layer of 10 neurons. All hidden layers use the Rectified Linear Unit (ReLU). We chose a **softmax** output layer with categorical cross-entropy as loss, because each image belongs to exactly one of six classes. It was trained for 10 epochs with the Adam optimizer." src="/assets/img/projects/deeplearning_baseline_en.svg" alt="Architecture of the baseline CNN: a greyscale camera image of 72 × 128 pixels passes three convolutional layers with 8 filters of 3 × 3, each followed by max pooling, then a dense layer of 10 neurons and a softmax layer that picks one of six states. No batch normalisation or dropout." full=true %}

{% include slide.html kicker="Method · Improved models" title="Towards the best model" text="Class weights (mistakes on rare classes count more) and data augmentation (varied copies of the training images) both made the baseline worse. After that the team worked on two separate lines.

**Teammates.** One teammate built **improved model v3**: more filters (32 to 256), a fourth convolutional layer, batch normalisation, dropout and L2 regularisation (90.9%). Another teammate ran a first hyperparameter search with **Optuna** on the baseline architecture itself: number of filters, kernel size, dense units, learning rate, optimizer and activation function (86.2%).

**My CNN.** I started from that first search and ran a second Optuna round with a narrower range around its best settings, now also searching the number of convolutional layers, batch size and dropout rate. That gave a deeper CNN with four convolutional layers, batch normalisation and dropout: 93.5% after 30 epochs. Adding L2 regularisation lowered the accuracy, so I removed it and raised the dropout to 0.25. The last step was doubling the filters in every layer (32 → 64 → 128 → 256): 95.1%. So the blue bars are one and the same model, step by step." src="/assets/img/projects/deeplearning_mpl_experimenten.png" alt="Horizontal bar chart of the best validation accuracy per experiment: baseline with class weights 45.6%, baseline with data augmentation 57.9%, baseline CNN 82.0%, improved model v3 by teammates 90.9%, Optuna round 1 on the baseline by a teammate 86.2%, and in blue my own line: Optuna round 2 with a deeper CNN 93.5% and the same CNN with filters 32 to 256 95.1%." full=true %}

{% include slide.html kicker="Method · Best model" title="The architecture of my CNN" text="Max pooling makes the feature maps smaller with depth, so I doubled the number of filters per layer to keep the amount of information. After every convolutional layer comes **batch normalisation**, which stabilises training, and **dropout** (0.25, and 0.3 before the output), which switches off random neurons so the network cannot memorise the training images. A final **softmax** layer turns the output into a probability for each of the six states. The model is trained with categorical cross-entropy and the Adam optimizer (learning rate 0.00032, batch size 64)." src="/assets/img/projects/deeplearning_cnn_en.svg" alt="Architecture of my CNN: a greyscale camera image of 72 × 128 pixels passes four convolutional layers with 32, 64, 128 and 256 filters of 5 × 5. Each is followed by batch normalisation; the first and third also by max pooling, the first three by dropout. Then dropout, dense layers of 60 and 30 neurons, dropout and a softmax layer that picks one of six states." full=true %}

{% include slide.html kicker="Method · Transfer learning" title="Reusing DenseNet121" text="For transfer learning we used DenseNet121, pretrained on ImageNet. It expects colour input, so the images were loaded as RGB. As the assignment required, its convolutional layers stayed frozen; only new dense layers on top were trained. Two dense layers with batch normalisation reached 79.3% validation accuracy, an extra and larger dense layer 83.1%. Because the validation accuracy kept jumping around, a learning-rate scheduler then halved the learning rate whenever the validation loss stopped improving for three epochs. That raised the best validation accuracy to 85.9%." src="/assets/img/projects/deeplearning_transfer_en.svg" alt="Diagram of transfer learning: a camera image of 72 × 128 pixels, loaded as RGB, passes the frozen, pretrained DenseNet121 (121 layers learned on ImageNet photos, weights not updated, shown in grey), then a pooling layer and three new dense layers of 512, 256 and 128 neurons with batch normalisation and dropout (trained, shown in blue), and a softmax layer that picks one of six driver states." full=true %}

{% include slide.html kicker="Results · Comparison" title="The three models compared, my CNN on top" text="All models were evaluated once on the 985 test images they had not seen. **Accuracy** is the share of images classified correctly. **Precision** is how often a predicted state is right, **recall** is the share of each state that is found and the **F1-score** combines the two. Each is averaged over the six states without weighting (macro average), so the rare states count as much as the common ones. My CNN scores best on every measure. DenseNet121 is better than the baseline, but stays well below my CNN.

My CNN reaches 95% accuracy on the test set and a macro-averaged recall of 0.92. All 26 yawning drivers are now recognised. 'Distracted' and 'safe driving' improved the most, but remain the most commonly confused pair (26 mix-ups instead of 78): a driver glancing aside looks very much like a driver looking at the road." src="/assets/img/projects/deeplearning_mpl_vergelijking.png" alt="Left: table of test results. Baseline CNN: accuracy 79%, precision 0.71, recall 0.65, F1-score 0.66. DenseNet121: 84%, 0.82, 0.73, 0.76. My CNN: 95%, 0.95, 0.92, 0.93. Right: confusion matrix of my CNN on the test set; 12 distracted drivers predicted as safe driving and 14 safe drivers as distracted, all 26 yawning drivers correct." full=true %}

{% include slide.html kicker="Results · Comparison" title="Why accuracy is not enough: recall per state" text="**Recall** is the share of drivers in a state that the model recognises: a recall of 0.80 for yawning means 8 of every 10 yawning drivers are flagged as yawning. Accuracy hides the rare states, because 42% of the test images are safe driving. A model that misses every yawning driver can still score high on accuracy. For a warning system those rare states matter most: a sleepy or yawning driver that goes unnoticed is exactly the risk.

The baseline recognised only 5 of the 26 yawning drivers (0.19). My CNN recognises all 26. For distracted drivers recall rose from 0.63 to 0.92. DenseNet121 barely improves on the baseline there (0.60)." src="/assets/img/projects/deeplearning_mpl_recall.png" alt="Grouped bar chart of recall per driver state on the test set for the baseline CNN, DenseNet121 and my CNN. Dangerous driving 0.93, 0.96, 0.99. Distracted 0.63, 0.60, 0.92. Drinking 0.60, 0.68, 0.80. Safe driving 0.81, 0.90, 0.95. Sleepy driving 0.71, 0.74, 0.84. Yawning 0.19, 0.50, 1.00." full=true %}

{% include slide.html kicker="Discussion" title="Strong, but not ready for the road" text="Transfer learning did worse than our own CNN, probably because DenseNet121 was pretrained on colour photos of everyday objects and, as the assignment required, its layers stayed frozen. Fine-tuning the last convolutional layers is a next step. Colour images or a higher resolution could also help, but the preprocessing was fixed by the assignment. Real use needs more than accuracy: the model must work equally well for all groups of drivers, and in-car cameras raise privacy and security questions." statement=true %}
