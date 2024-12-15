# Motor Imagery Classification Using EEG Signals

This repository contains the implementation of models for motor imagery classification using EEG data, focusing on leveraging advanced neural network architectures such as EEGNet and Multi-Branch CNNs. The project utilizes the BCICIV 2a dataset and explores future directions with Graph Neural Networks (GNNs).

## Table of Contents
- [Introduction](#introduction)
- [Dataset](#dataset)
- [Model Architectures](#model-architectures)
- [Results](#results)
- [Future Work](#future-work)
- [Getting Started](#getting-started)
- [License](#license)

## Introduction
Motor imagery classification is a key component of Brain-Computer Interface (BCI) systems. It enables communication between the brain and external devices by interpreting EEG signals corresponding to imagined physical movements (e.g., moving a hand or foot). This project aims to enhance classification accuracy using advanced machine learning techniques.

## Dataset
The BCICIV 2a dataset is used in this project. Key features include:
- EEG recordings from 9 subjects.
- 4 motor imagery tasks: left hand, right hand, feet, tongue.
- Sampling rate: 250 Hz.
- Duration: 4 seconds per trial, resulting in 1001 timesteps per trial.

The dataset is balanced across all tasks and subjects but exhibits significant inter-subject variability, making generalization a challenge.

## Model Architectures
### EEGNet
- A lightweight convolutional neural network designed for EEG data.
- Employs depthwise and separable convolutions to efficiently extract spatial and temporal features.
- Limitations: Overfitting (train accuracy: 90%, test accuracy: 70%), sensitivity to noise.

### Multi-Branch CNN
Two variations are explored:
1. **Frequency-Domain Branches**:
   - Separate branches for Alpha (8--12 Hz), Beta (13--30 Hz), and Gamma (30--80 Hz) frequency bands.
   - Each branch processes frequency-specific features using 1D convolutions.

2. **Spatial-Temporal Branches**:
   - A spatial branch using 2D convolutions to model inter-channel relationships.
   - A temporal branch using 1D convolutions for temporal dynamics.

## Results
The best hyperparameters and test accuracies for each model are summarized below:

| Model              | Variation           | Learning Rate | Dropout Rate | Test Accuracy |
|--------------------|---------------------|---------------|--------------|---------------|
| EEGNet             | N/A                 | 0.001         | 0.3          | 70.0%         |
| Multi-Branch CNN   | Frequency-Domain    | 0.0005        | 0.4          | 73.5%         |
| Multi-Branch CNN   | Spatial-Temporal    | 0.0005        | 0.4          | 75.0%         |

## Future Work
The next phase of this project involves integrating the feature extraction capabilities of EEGNet and autoencoders with Graph Neural Networks (GNNs). GNNs offer the following advantages:
- **Feature Enrichment**: Graph representations of spatial and temporal EEG features for enhanced learning.
- **Improved Generalization**: Better handling of inter-subject variability.
- **Current Progress**: Initial experiments are underway, focusing on tuning and validating GNNs for EEG-based classification.
