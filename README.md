# Pneumonia Diagnosis Detection and Localization

## Team Members

- Vidhwath S — PES2UG24AM182
- Varun C H — PES2UG24AM180

---

## 1. Project Overview

This project focuses on detecting Lung Opacity in chest X-ray images using a custom Convolutional Neural Network (CNN) and providing weakly supervised localization of the detected regions.

The classification model is trained entirely from scratch without using pretrained models, ImageNet weights, or transfer learning.

Grad-CAM is used to generate class-discriminative heatmaps from the trained CNN. These heatmaps are converted into predicted bounding boxes and compared with the ground-truth annotations using Intersection over Union (IoU).

The project is based on the RSNA Pneumonia Detection Challenge dataset.

---

## 2. Problem Statement

Chest X-ray interpretation can be challenging because abnormal lung regions may vary considerably in size, shape, and location.

The objective of this project is to develop a machine learning system that:

1. Classifies chest X-rays into Normal and Lung Opacity classes.
2. Uses Grad-CAM to identify regions that contribute to the model's prediction.
3. Converts the Grad-CAM activation maps into bounding boxes.
4. Evaluates the overlap between predicted and ground-truth regions using IoU.

---

## 3. Dataset

The project uses the RSNA Pneumonia Detection Challenge dataset.

The dataset contains chest X-ray images and annotations for lung opacity regions.

For this implementation, a balanced subset of 2,000 images was selected:

- 1,000 Normal images
- 1,000 Lung Opacity images

The dataset was divided into:

| Split | Number of Images |
|---|---:|
| Training | 1,400 |
| Validation | 300 |
| Test | 300 |

Images classified as `No Lung Opacity / Not Normal` were excluded from the binary classification task.

Duplicate patient IDs were also removed before sampling the final dataset.

---

## 4. Data Preprocessing

The chest X-ray DICOM images were:

- Loaded from the RSNA dataset.
- Normalized to an intensity range of 0–255.
- Converted from grayscale to RGB.
- Resized to 224 × 224 pixels.
- Normalized using mean = 0.5 and standard deviation = 0.5.

Training images additionally used:

- Random horizontal flipping
- Random rotation

These augmentations were applied only to the training set.

---

## 5. Model Architecture

A custom CNN was designed and trained from scratch.

The architecture consists of:

- 4 convolutional layers
- ReLU activation functions
- Max-pooling layers
- Global Average Pooling
- Dropout
- Fully connected classification layer

The final layer produces two class outputs:

- Normal
- Lung Opacity

No pretrained model or transfer learning was used.

---

## 6. Model Training

The model was trained using:

- Loss function: Cross-Entropy Loss
- Optimizer: Adam
- Learning rate: 0.001
- Batch size: 32
- Number of epochs: 5

The validation set was used to monitor model performance during training.

---

## 7. Classification Results

The trained model was evaluated on the unseen test set.

| Metric | Result |
|---|---:|
| Accuracy | 78.67% |
| Precision | 76.88% |
| Recall | 82.00% |
| F1 Score | 79.35% |
| ROC-AUC | 82.07% |

### Confusion Matrix

The test-set confusion matrix was:

```text
[[113, 37],
 [ 27, 123]]
