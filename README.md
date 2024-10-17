## Introduction
This repository contains my work on detection and segmentation using YOLOv8, conducted under the guidance of [Prof. Dr. Khurram Khan Jadoon](https://scholar.google.com/citations?user=LbkI6C0AAAAJ&hl=en). The project focuses on experimenting with the YOLOv8 architecture for object detection and segmentation, specifically aimed at detecting guns in images. Throughout this project, I explored how model fine-tuning, segmentation, and detection work, while analyzing the impact of modifications on model performance.

## Project Overview

### Detection
- **Base Model**: YOLOv8n.pt
- [**Dataset**:](https://github.com/abdullahejazjanjua/Yolov8_detection_segmentation/blob/main/Detection/data.txt) The dataset consists of images with a single object class, **'gun'**.

#### Modifications
- [Experimented](https://github.com/abdullahejazjanjua/Yolov8_detection_segmentation/tree/main/Detection/Notebooks/Detection_on_modified_yolo) with hyperparameters to observe their effects on detection accuracy.
- Added and removed C2f and Conv layers to explore architectural changes.
- **Impact**: Most modifications led to a drop in Precision and Recall, offering insight into the sensitivity of the model to structural changes.

#### Performance
- **Best Results**: [Detection Best Results](https://github.com/abdullahejazjanjua/Yolov8_detection_segmentation/blob/main/Detection/Notebooks/Detection_on_default_yolo/detection_best.ipynb)
- **Metrics**:
  - Precision: 0.8706
  - Recall: 0.8000
  - mAP@50: 0.8273
  - mAP@50-95: 0.4708

### Segmentation
- **Base Model**: YOLOv8n-seg.pt
- [**Dataset**:](https://github.com/abdullahejazjanjua/Yolov8_detection_segmentation/blob/main/Segmentation/data.txt) Annotated with segmentation masks created using RoboFlow.

#### Modifications
- [Experimentations](https://github.com/abdullahejazjanjua/Yolov8_detection_segmentation/tree/main/Segmentation/Segmentation_experimentations.ipynb) with different hyperparameters to evaluate segmentation performance for the 'gun' class.

#### Performance
- **Best Results**: [Segmentation Best Results](https://github.com/abdullahejazjanjua/Yolov8_detection_segmentation/blob/main/Segmentation/Notebooks/Segmentation_frozen_layers.ipynb)
- **Metrics**:
  - Precision: 0.9937
  - Recall: 0.7000
  - mAP@50: 0.8432
  - mAP@50-95: 0.5908
  - Box Precision: 0.8679
  - Box Recall: 0.8000
  - Mask Precision: 0.9177
  - Mask Recall: 0.3290

## Model Architecture Breakdown

1. **Input Image through Conv and C2f Layers**  
   - **Conv**: Extracts key features.
   - **C2f**: Refines extracted features and enhances gradient flow.

2. **SPPF for Multi-scale Feature Extraction**  
   - Creates a feature pyramid from different scales to handle objects of varying sizes.

3. **Detection Module**  
   - Predicts bounding boxes at each scale and applies NMS to retain the highest confidence prediction.

4. **Proto Layer for Pixel-wise Object Scores**  
   - Generates pixel-wise object scores to create segmentation masks on the feature map.

5. **Segmentation Module**  
   - Extracts segmentation masks corresponding to predicted bounding boxes.
   - Converts these masks into binary format and upscales them to match the original image size.

## Conclusion
This project was an educational journey into fine-tuning YOLOv8 for detection and segmentation tasks. By experimenting with various model structures and hyperparameters, I gained valuable insights into how detection and segmentation models operate, particularly for gun detection.
