# Lane Detection using Pre-Trained CNN (PyTorch + TuSimple)

This project implements an AI-based lane detection system using a pre-trained Convolutional Neural Network (CNN) fine-tuned on the TuSimple dataset. The system is designed to improve lane detection accuracy under varied real-world driving conditions, making it useful for autonomous vehicles and driver assistance technologies.

---

## Table of Contents
- [Introduction](#introduction)
- [Dataset and Preprocessing](#dataset-and-preprocessing)
- [Model Architecture](#model-architecture)
- [Training Strategy](#training-strategy)

---

## 1. Introduction

Lane detection is a critical component of self-driving and driver assistance systems. Traditional computer vision methods struggle in dynamic environments. This project uses transfer learning with a ResNet-18 architecture, fine-tuned to identify lanes from road images. PyTorch is used for model development and training.

---

## 2. Dataset and Preprocessing

### 2.1 TuSimple Dataset

The TuSimple dataset contains:
- Road images from a front-facing vehicle camera
- JSON labels with lane coordinates
- Scenes with different lighting and weather conditions

### 2.2 Data Preparation

- Images resized to fixed CNN input dimensions
- Pixel value normalization
- Data augmentation: random crop, brightness changes, horizontal flips
- Annotation parsing and mask generation
- Data loading using PyTorch DataLoader for batch processing

---

## 3. Model Architecture

### 3.1 Base Model: ResNet-18

- Pre-trained on ImageNet
- Final fully connected layer replaced with custom output for lane prediction

### 3.2 Modifications

- Custom output suited for coordinate/mask prediction
- Dropout for regularization
- Output reshaped for visual or coordinate-based detection

---

## 4. Training Strategy

### 4.1 Hyperparameters

- Loss function: Binary Cross-Entropy (BCE)
- Optimizer: Adam
- Batch size: 16
- Epochs: 20 with early stopping

### 4.2 Workflow

1. Input images are passed through the CNN
2. Outputs are compared with ground truth to compute loss
3. Gradients are calculated and weights updated
4. Performance is evaluated on a validation set

### 4.3 Hardware

- Training accelerated using GPU for faster processing
- Batch loading optimized for performance

---


