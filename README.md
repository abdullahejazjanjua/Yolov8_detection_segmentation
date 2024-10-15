# Yolov8_detection_segmentation
This repository contains my work on Detection and Segmentation using YOLOv8.
Here's an improved README for your project, including details about both detection and segmentation with YOLOv8. I've added sections for segmentation and refined the overall structure and wording.

---

# YOLOv8 Detection and Segmentation

## Introduction
This repository contains my work on detection and segmentation using YOLOv8. The project focuses on experimenting with the YOLOv8 architecture for object detection and segmentation, particularly aimed at detecting guns in images. Modifications were made to the model architecture, and their impacts on performance were analyzed.

## Project Overview

### Detection
- **Base Model**: YOLOv8n.pt
- [**Dataset**](https://github.com/abdullahejazjanjua/Yolov8_detection_segmentation/blob/main/Detection/data.txt): The dataset consists of images with guns as the primary object class, with detection based on a single class: **'gun'**.

#### Modifications
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
- [**Dataset**](https://github.com/abdullahejazjanjua/Yolov8_detection_segmentation/blob/main/Segmentation/data.txt): The same dataset was used, but it was annotated by creating masks for each image using RoboFlow.

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

## Conclusion
This project demonstrates the versatility of YOLOv8 in both detection and segmentation tasks. Through various modifications to the model architecture and hyperparameters, I aimed to optimize performance for detecting and segmenting firearms. 