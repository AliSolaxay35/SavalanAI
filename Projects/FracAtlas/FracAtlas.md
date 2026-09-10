# FracAtlas — Fracture Segmentation With U-Net

A Lightweight Medical Image Segmentation Project Using U-Net To Localize And Segment Fracture Regions In X-Ray Images.

## Overview

FracAtlas Is A Medical Imaging Segmentation Experiment Built Around The FracAtlas Dataset.

The Project Uses COCO-Format Fracture Annotations To Generate Pixel-Level Ground Truth Masks And Trains A Lightweight U-Net Model To Predict Fracture Regions In X-Ray Images.

The Main Goal Of This Project Is To Explore Medical Image Segmentation, Medical Image Annotation Processing, Pixel-Level Prediction, And Evaluation Using Dice And IoU Metrics.

## Dataset

The FracAtlas Dataset Contains X-Ray Images With Fracture-Related Annotations.

For This Project, COCO Segmentation Annotations Are Used To Generate Pixel-Level Ground Truth Masks.

### Dataset Statistics

* Total Images: 4,083
* Annotated Images: 717
* Total Annotations: 922
* Annotation Category: `fractured`
* Maximum Annotations Per Image: 5
* Average Annotations Per Annotated Image: 1.29

The Dataset Is Downloaded Automatically During Notebook Execution Using KaggleHub.

## Model

A Lightweight U-Net Architecture Is Used For Fracture Segmentation.

### Architecture

* Input Channels: 1
* Encoder Channels: 16 → 32 → 64
* Bottleneck Channels: 128
* Decoder Channels: 64 → 32 → 16
* Output Channels: 1
* Batch Normalization
* ReLU Activation
* Dropout2D
* Transposed Convolution Upsampling

The Model Is Designed To Remain Lightweight While Providing A Practical Segmentation Baseline.

## Training

The Model Was Developed And Trained Using Google Colab With An NVIDIA T4 GPU.

### Configuration

| Parameter             |                    Value |
| --------------------- | -----------------------: |
| Image Size            |                384 × 384 |
| Batch Size            |                        8 |
| Epochs                |                       20 |
| Initial Learning Rate |                     3e-4 |
| Optimizer             |                    AdamW |
| Weight Decay          |                     1e-5 |
| Loss                  | Weighted BCE + Dice Loss |
| Scheduler             |        ReduceLROnPlateau |
| Early Stopping        |                  Enabled |
| Random Seed           |                       42 |

The Complete Training Run Took Approximately 6 Minutes On An NVIDIA T4 GPU.

CPU Training Was Significantly Slower, Taking Approximately 13 Minutes Per Epoch In The Same Environment.

## Results

The Best Validation Performance Was Obtained At Epoch 17.

| Metric                     | Result |
| -------------------------- | -----: |
| Best Validation Dice @ 0.5 | 0.3217 |
| Optimized Threshold        |   0.75 |
| Validation Dice @ 0.75     | 0.3598 |
| Validation IoU             | 0.2572 |
| Validation Precision       | 0.3969 |
| Validation Recall          | 0.4942 |
| Predicted Foreground       |  0.68% |

The Optimized Threshold Was Selected By Evaluating Multiple Thresholds Between 0.10 And 0.90.

## Visual Results

Sample Images Are Included To Demonstrate The Fracture Bounding Box, Ground Truth Segmentation Mask, Training History, And Model Prediction.

## Model Release

The Best Trained Model Is Provided As A GitHub Release Asset:

`savalanai_fracatlas_unet_best.pth`

The Model File Is Not Directly Committed To The Repository.

## Project Documentation

The Repository Includes The Complete Google Colab Notebook, Technical Documentation, Sample Visualizations, And The Best Trained Model Through The GitHub Release.

## Technologies

* Python
* Google Colab
* PyTorch
* Torchvision
* NumPy
* Pandas
* Matplotlib
* PIL
* Scikit-Learn
* KaggleHub
* COCO Annotations
* U-Net
* Medical Image Segmentation

## Project Status

**Completed**

FracAtlas Serves As A Lightweight Medical Image Segmentation Experiment And A Practical Study Of Fracture Segmentation Using U-Net.

## Disclaimer

This Project Is Intended For Educational And Research Purposes Only.

The Model Has Not Been Validated For Clinical Diagnosis Or Medical Decision-Making.
