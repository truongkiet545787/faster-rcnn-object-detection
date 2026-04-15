Object Detection with Faster R-CNN
📖 Overview

This project implements an object detection model using Faster R-CNN with MobileNetV3 backbone. The goal is to detect and classify objects in images with high accuracy while maintaining lightweight computation.

 Dataset

The model is trained on the Pascal VOC dataset (or custom dataset with similar format).

Annotation format: XML (bounding boxes + labels)
Number of classes: 20
Data split: Train / Validation
Each image contains multiple objects with corresponding bounding boxes
⚙️ Preprocessing
Resize images to a fixed size (e.g., 320x320)
Normalize using ImageNet statistics
Convert annotations to tensors (boxes, labels)

Data Augmentation:

Random Horizontal Flip
Random Crop
Color Jitter
 Model
Architecture: Faster R-CNN
Backbone: MobileNetV3 + FPN
Components:
Region Proposal Network (RPN)
ROI Head (classification + bounding box regression)

Customization:

Adjusted number of output classes
Fine-tuned for detection task🚀 Training
Optimizer: SGD
Learning rate: 0.001
Momentum: 0.9
Batch size: 8
Epochs: 10

Logging: TensorBoard
Checkpoint: Best model saved during training

 Evaluation
Metric: mAP (mean Average Precision)
Monitored loss and performance across epochs
 Demo / Inference

Pipeline:

Load trained model
Input image
Predict bounding boxes & labels
Visualize results

Output:

Bounding boxes
Class labels
Confidence scores

 Requirements
torch
torchvision
opencv-python
numpy
matplotlib
tensorboard
