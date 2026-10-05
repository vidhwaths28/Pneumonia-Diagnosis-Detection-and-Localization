# Pneumonia Diagnosis Detection and Localization

## Team Members

- Vidhwath S – PES2UG24AM182
- Varun C H – PES2UG24AM180

## Project Overview

This project develops a custom Convolutional Neural Network (CNN) for classifying chest X-ray images into Normal and Lung Opacity classes and provides weakly supervised localization of opacity regions.

The model is trained entirely from scratch without using pretrained models, ImageNet weights, or transfer learning.

Grad-CAM is used to generate class-discriminative heatmaps from the trained CNN. These heatmaps are converted into predicted bounding boxes and compared with ground-truth annotations using Intersection over Union (IoU).

The project uses the RSNA Pneumonia Detection Challenge dataset.

## Problem Statement

The objective of this project is to develop a machine learning system that:

1. Classifies chest X-rays into Normal and Lung Opacity classes.
2. Uses Grad-CAM to identify image regions contributing to the prediction.
3. Converts Grad-CAM activation maps into bounding boxes.
4. Evaluates predicted regions against ground-truth regions using IoU.

## Dataset

The RSNA Pneumonia Detection Challenge dataset contains chest X-ray images and corresponding annotations.

For this project, a balanced subset of 2,000 images was used:

- 1,000 Normal images
- 1,000 Lung Opacity images

The data was divided into:

- Training: 1,400 images
- Validation: 300 images
- Testing: 300 images

## Methodology

The project consists of the following stages:

1. Dataset preparation and preprocessing
2. Custom CNN design
3. Training from scratch
4. Binary classification evaluation
5. Grad-CAM generation
6. Bounding-box localization
7. IoU evaluation
8. Grad-CAM threshold experimentation

## Model

A custom CNN with four convolutional layers was designed.

Architecture:

- Conv2D: 3 → 32 channels
- Conv2D: 32 → 64 channels
- Conv2D: 64 → 128 channels
- Conv2D: 128 → 256 channels
- Global Average Pooling
- Dropout
- Fully Connected classification layer

The model was trained using:

- Loss: Cross Entropy Loss
- Optimizer: Adam
- Learning rate: 0.001
- Epochs: 5

## Results

The final model achieved:

| Metric | Result |
|---|---:|
| Accuracy | 78.67% |
| Precision | 76.88% |
| Recall | 82.00% |
| F1 Score | 79.35% |
| ROC-AUC | 82.07% |

The confusion matrix was:

```text
[[113, 37],
 [ 27, 123]]
