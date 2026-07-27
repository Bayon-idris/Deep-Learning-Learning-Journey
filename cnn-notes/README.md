# CNN Architectures — Notes

A collection of concise notes about influential architectures that shaped modern computer vision.

The goal is not to cover every CNN architecture ever proposed, but to understand the main ideas that introduced important changes in visual recognition.

Each note focuses on:

- the problem the architecture solved,
- the main innovation,
- how the architecture works,
- trade-offs,
- limitations,
- and ideas that were kept or replaced by later models.


---

# Important Note About Architecture Diagrams

The architecture diagrams presented here are simplified representations of the original models.

Many famous architectures evolved through multiple versions:

- ResNet: ResNet-18, ResNet-34, ResNet-50, ResNet-101, ResNet-152
- Inception: GoogLeNet, Inception-v2, Inception-v3, Inception-v4
- MobileNet: MobileNetV1, MobileNetV2, MobileNetV3
- EfficientNet: EfficientNet-B0 to EfficientNet-B7, EfficientNetV2

The figures shown in this repository may represent a specific variant or a generalized overview of the architecture family.

For complete details, implementation differences, and official experimental results, readers should always refer to the original research papers.


---

# Architectures Covered

| Architecture | Year | Main Contribution |
|---|---:|---|
| LeNet-5 | 1998 | Automatic feature extraction using convolution and pooling |
| AlexNet | 2012 | Demonstrated the power of deep CNNs with GPUs and large datasets |
| VGG | 2014 | Simple deep networks built with repeated 3×3 convolutions |
| Inception (GoogLeNet) | 2014 | Multi-scale feature extraction with parallel branches |
| ResNet | 2015 | Residual connections enabling very deep networks |
| MobileNet | 2017 | Efficient CNNs using depthwise separable convolutions |
| EfficientNet | 2019 | Balanced scaling of depth, width, and resolution |
| Vision Transformer | 2020 | Replacing convolution with self-attention for vision tasks |


---

# Beyond CNN Classification

These architectures represent only a small part of modern computer vision.

Other important areas include:

- Object Detection
    - YOLO
    - Faster R-CNN
    - DETR

- Semantic Segmentation
    - U-Net
    - DeepLab
    - SegFormer

- Instance Segmentation

- Pose Estimation

- Video Understanding

- Vision-Language Models


---

# Image Attribution

Architecture diagrams are collected from publicly available educational sources.

They are included only for learning purposes.

The original papers remain the primary reference for each architecture.