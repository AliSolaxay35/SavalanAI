# Retinal-OCT — Retinal OCT Classification With ResNet18

A Medical Imaging Classification Project Using A Pretrained ResNet18 Model To Classify Retinal Optical Coherence Tomography (OCT) Images Into Eight Classes. 🧠👁️

## Overview

Retinal-OCT Is A Medical Imaging Deep Learning Project Focused On Multi-Class Classification Of Retinal OCT Images.

The Project Uses A Pretrained ResNet18 Architecture And Fine-Tunes Its Final Classification Layer For Eight Retinal OCT Classes.

The Complete Workflow Includes Dataset Download, Dataset Exploration, Class Distribution Analysis, Sample Visualization, Image Preprocessing, Transfer Learning, Model Training, Validation, Test Evaluation, Classification Report, Confusion Matrix, And Single-Image Prediction.

## Dataset

The Project Uses The Retinal OCT Image Classification — C8 Dataset.

The Dataset Contains Eight Classes:

* AMD
* CNV
* CSR
* DME
* DR
* DRUSEN
* MH
* NORMAL

The Dataset Is Organized Into Separate Training, Validation, And Test Directories And Is Downloaded Automatically Using KaggleHub. The Notebook Dynamically Locates The Required Dataset Directories After Download.

### Dataset Distribution

| Class  | Train | Validation | Test |
| ------ | ----: | ---------: | ---: |
| AMD    | 2,300 |        350 |  350 |
| CNV    | 2,300 |        350 |  350 |
| CSR    | 2,300 |        350 |  350 |
| DME    | 2,300 |        350 |  350 |
| DR     | 2,300 |        350 |  350 |
| DRUSEN | 2,300 |        350 |  350 |
| MH     | 2,300 |        350 |  350 |
| NORMAL | 2,300 |        350 |  350 |

This Results In 18,400 Training Images, 2,800 Validation Images, And 2,800 Test Images. The Notebook Confirms An Equal Distribution Across All Eight Classes.

## Model

The Project Uses A Pretrained ResNet18 Model From Torchvision.

The Original Final Fully Connected Layer Is Replaced With A New Classification Layer Producing Eight Output Classes.

### Model Configuration

* Architecture: ResNet18
* Pretrained Weights: Torchvision Default Weights
* Input Size: 224 × 224
* Output Classes: 8
* Classification Layer: Linear
* Loss Function: CrossEntropyLoss
* Optimizer: AdamW
* Learning Rate: 1e-4
* Weight Decay: 1e-4
* Scheduler: ReduceLROnPlateau

## Data Preprocessing

Training Images Are Resized To 224 × 224 And Processed Using Data Augmentation Before Being Passed To The Model.

The Evaluation Pipeline Uses The Corresponding Image Preprocessing Without Training Augmentation.

The Model Uses ImageNet Normalization Because The ResNet18 Backbone Is Initialized With Pretrained ImageNet Weights.

## Training

The Model Was Developed And Trained Using Google Colab With An NVIDIA Tesla T4 GPU. ⚡

### Training Configuration

| Parameter             |             Value |
| --------------------- | ----------------: |
| Image Size            |         224 × 224 |
| Batch Size            |                64 |
| Epochs                |                10 |
| Initial Learning Rate |              1e-4 |
| Weight Decay          |              1e-4 |
| Optimizer             |             AdamW |
| Loss                  |  CrossEntropyLoss |
| Scheduler             | ReduceLROnPlateau |
| Random Seed           |                42 |
| Device                |   NVIDIA Tesla T4 |

The Training Process Saved The Model Whenever A New Best Validation Accuracy Was Achieved. The Best Validation Accuracy Was Reached At Epoch 10 With 97.39%.

## Results

The Final Model Achieved Strong Performance On The Held-Out Test Set.

### Overall Results

| Metric                   | Result |
| ------------------------ | -----: |
| Best Validation Accuracy | 97.39% |
| Test Accuracy            | 97.79% |
| Macro F1-Score           | 97.78% |
| Weighted F1-Score        | 97.78% |
| Test Samples             |  2,800 |

The Test Set Classification Report Shows Balanced Performance Across The Eight Classes.

### Class-Level Performance

| Class  | Precision |  Recall | F1-Score |
| ------ | --------: | ------: | -------: |
| AMD    |   100.00% | 100.00% |  100.00% |
| CNV    |    94.63% |  95.71% |   95.17% |
| CSR    |   100.00% | 100.00% |  100.00% |
| DME    |    97.35% |  94.57% |   95.94% |
| DR     |   100.00% | 100.00% |  100.00% |
| DRUSEN |    95.63% |  93.71% |   94.66% |
| MH     |   100.00% | 100.00% |  100.00% |
| NORMAL |    94.77% |  98.29% |   96.49% |

The Confusion Matrix Is Also Included In The Notebook To Provide A More Detailed View Of Class-Level Predictions.

## Visual Results

The Project Includes Sample Visualizations Demonstrating:

* Dataset Samples
* Training History
* Test Predictions
* Single-Image Prediction

The Prediction Visualization Displays True And Predicted Labels For Test Images.

## Model Release

The Best Trained Model Is Released Separately As A GitHub Release Asset:

`savalanai_oct_c8_resnet18_best.pth`

The Model File Is Approximately 43.8 MB And Is Not Directly Committed To The Repository.

## Project Files

The Project Contains The Complete Google Colab Notebook, Dedicated Documentation, Requirements File, And Sample Visualization Images.

The Trained Model Is Distributed Through The GitHub Release Rather Than The Main Repository.

## Technologies

* Python
* Google Colab
* PyTorch
* Torchvision
* ResNet18
* NumPy
* Pandas
* Matplotlib
* Pillow
* Scikit-Learn
* KaggleHub
* Medical Imaging
* Retinal OCT
* Transfer Learning
* Image Classification

## Project Status

**Completed** ✅

Retinal-OCT Serves As A Practical Medical Imaging Classification Experiment Using Transfer Learning With ResNet18.

## Disclaimer

This Project Is Intended For Educational And Research Purposes Only.

The Model Has Not Been Clinically Validated And Must Not Be Used For Medical Diagnosis, Patient Management, Or Clinical Decision-Making.
