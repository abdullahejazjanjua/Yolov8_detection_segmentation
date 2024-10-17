# YOLOv8 Detection and Segmentation Project

## Table of Contents
- [Introduction](#introduction)
- [Project Overview](#project-overview)
  - [Detection](#detection)
  - [Segmentation](#segmentation)
- [Model Architecture Explanation](#model-architecture-explanation)
- [Conclusion](#conclusion)

## Introduction
This repository contains my work on detection and segmentation using YOLOv8, conducted under the guidance of [Prof. Dr. Khurram Khan Jadoon](https://scholar.google.com/citations?user=LbkI6C0AAAAJ&hl=en). The project focuses on experimenting with the YOLOv8 architecture for object detection and segmentation, specifically aimed at detecting guns in images. Throughout this project, I explored how model fine-tuning, segmentation, and detection work, while analyzing the impact of modifications on model performance.

## Project Overview

### Detection
- **Base Model**: YOLOv8n.pt
- [**Dataset**:](https://github.com/abdullahejazjanjua/Yolov8_detection_segmentation/blob/main/Detection/data.txt) The dataset consists of images with guns as the primary object class, with detection based on a single class: **'gun'**.

#### Modifications
[Experimentations](https://github.com/abdullahejazjanjua/Yolov8_detection_segmentation/tree/main/Detection/Notebooks/Detection_on_modified_yolo)
- Experimented with various hyperparameters.
- Added C2f layers at the end of the model.
- Removed C2f and Conv layers in pairs from both the initial and final stages.
- **Impact**: All modifications affected Precision and metrics, mostly leading to a decrease in performance.

#### Performance
- **Best Results**: [Detection Best Results](https://github.com/abdullahejazjanjua/Yolov8_detection_segmentation/blob/main/Detection/Notebooks/Detection_on_default_yolo/detection_best.ipynb)
- **Metrics**:
  - Precision: 0.8706
  - Recall: 0.8000
  - mAP@50: 0.8273
  - mAP@50-95: 0.4708

### Segmentation
- **Base Model**: YOLOv8n-seg.pt
- [**Dataset**:](https://github.com/abdullahejazjanjua/Yolov8_detection_segmentation/blob/main/Segmentation/data.txt) The same dataset was used, but it was annotated by creating masks for each image using RoboFlow.

#### Modifications
[Experimentations](https://github.com/abdullahejazjanjua/Yolov8_detection_segmentation/tree/main/Segmentation/Segmentation_experimentations.ipynb)
- Experimented with different hyperparameters similar to detection.
- Evaluated the model's ability to segment the 'gun' class effectively.

#### Performance
- **Best Results**: [Segmentation Best Results](https://github.com/abdullahejazjanjua/Yolov8_detection_segmentation/blob/main/Segmentation/Notebooks/Segmentation_frozen_layers.ipynb)
- **Metrics**:
    - Precision: 0.9937
    - Recall: 0.7
    - mAP@50: 0.8432
    - mAP@50-95: 0.5908
    - Box Precision: 0.8679
    - Box Recall: 0.8
    - Mask Precision: 0.9177
    - Mask Recall: 0.3290

## Model Architecture Explanation

1. **Input Image through Conv and C2f Layers**  
   - **Conv**: Extracts key features.  
   - **C2f**: Refines these features and improves gradients.

2. **SPPF for Multi-scale Feature Extraction**  
   - Scales the feature map at different levels.  
   - Produces a concatenated feature map (feature pyramid) from different scales.

3. **Detection Module**  
   - Predicts bounding boxes at each level/scale.  
   - Uses NMS to retain the highest confidence bounding box for each object.

4. **Proto Layer for Pixel-wise Object Scores**  
   - Assigns pixel-wise object scores for the entire image, producing segmentation masks on the feature map.

5. **Segmentation Module**  
   - Extracts the segmentation mask corresponding to the predicted bounding box.  
   - Converts the segmentation mask into a binary mask.  
   - Upscales the mask to match the original image dimensions before outputting the final result.

## Conclusion
This project demonstrates the versatility of YOLOv8 in both detection and segmentation tasks. Through various modifications to the model architecture and hyperparameters, I aimed to optimize performance for detecting and segmenting firearms.
