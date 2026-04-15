Object Detection with Faster R-CNN
Overview

This project implements an object detection model using Faster R-CNN with MobileNetV3 backbone. The goal is to detect and classify objects in images with good accuracy while keeping the model lightweight.

Dataset

The model is trained on the Pascal VOC dataset (or a similar custom dataset).

Annotation format: XML (bounding boxes and labels)

Number of classes: 20

Data split: Train / Validation

Each image may contain multiple objects

Preprocessing



Normalize using ImageNet mean and std

Convert annotations to tensors (boxes, labels)



Model
Architecture: Faster R-CNN

Backbone: MobileNetV3 with FPN

Components:
Region Proposal Network (RPN)

ROI Head (classification and bounding box regression)

The model is customized by adjusting the number of output classes.

Training
Optimizer: SGD

Learning rate: 0.001

Momentum: 0.9

Batch size: 8

Epochs: 10

TensorBoard is used for logging.

The best model is saved during training as a checkpoint.

Evaluation

Metric: mAP (mean Average Precision)

Track both loss and mAP during training

Demo / Inference

Pipeline:

Load trained model

Input an image

Predict bounding boxes and labels

Visualize results

Output includes bounding boxes, class labels, and confidence scores.

Project Structure

project/

data/

checkpoint/

runs/

notebook.ipynb or train.py

README.md

requirements.txt

Requirements

torch

torchvision

opencv-python

numpy

matplotlib

tensorboard

Future Improvements
Train with larger dataset

Try stronger backbones (ResNet, EfficientNet)

Improve inference speed

Deploy using Streamlit or Flask
