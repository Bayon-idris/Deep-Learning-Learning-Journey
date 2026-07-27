# VGG-16 / VGG-19 (Simonyan & Zisserman, 2014)

![VGG Architecture](/assets/architectures/cnn/vgg_architecture.webp)

## 1. Problem it solves

AlexNet demonstrated that deep convolutional neural networks could achieve outstanding performance on ImageNet, but its architecture was relatively irregular, using different filter sizes (11×11, 5×5, and 3×3) and relying heavily on large fully connected layers. VGG addresses a simple question: **can a much deeper network built from a single, consistent building block achieve even better performance?**


## 2. Main idea

Instead of mixing different convolution sizes, VGG uses the same building block throughout the network: several **3×3 convolutional layers** followed by a **2×2 max-pooling layer**. By repeatedly stacking these simple blocks, VGG increases depth while keeping the architecture clean, uniform, and easy to understand.


## 3. How it works

* Input image size: **224 × 224 × 3**.
* The network is composed of **five convolutional blocks**.
* Each block contains **two or three 3×3 convolutions** followed by a **2×2 max-pooling** operation.
* After every pooling layer, the spatial resolution decreases while the number of feature maps increases (64 → 128 → 256 → 512 → 512).
* The extracted features are finally passed through **three fully connected layers** before the Softmax classifier.

The key idea is that stacking multiple small **3×3 convolutions** provides a receptive field similar to larger filters (such as 5×5 or 7×7), while requiring fewer parameters and introducing more non-linearities through additional ReLU activations.


## 4. Trade-off

VGG achieves significantly higher accuracy than AlexNet thanks to its increased depth and simple design. However, this comes at the cost of a **very large number of parameters** (approximately **138 million** for VGG-16), making the network computationally expensive and memory-intensive. While its uniform architecture makes it easy to understand and extend, it is much slower than many later CNN architectures.

## 5. Limitation

* The three large fully connected layers account for most of the model's parameters and memory usage.
* Increasing the depth further becomes difficult because VGG does not include skip connections, making optimization harder.
* The architecture only processes one convolutional scale at a time, unlike later models such as Inception that analyze multiple scales simultaneously.
* Due to its high computational cost, VGG is not well suited for mobile, embedded, or real-time applications.


## 6. Kept vs. abandoned later

* **Kept:** the use of small **3×3 convolutions**, repeating convolutional blocks, gradually increasing the number of feature channels, and using VGG as a pretrained backbone for transfer learning.
* **Abandoned:** the massive fully connected layers, the extremely high parameter count, and the absence of skip connections or multi-branch modules. Modern architectures replaced these with techniques such as **Global Average Pooling**, **Residual Connections**, and **multi-branch designs** to improve both efficiency and performance.


## 7. Can I explain it in 2 minutes without notes?

After AlexNet proved that deep convolutional neural networks could achieve excellent performance on large-scale image classification, researchers wondered whether simply making CNNs deeper could further improve accuracy. This question led to VGG, introduced by the Visual Geometry Group at Oxford in 2014.

The main idea behind VGG was simplicity. Instead of using large convolution filters like AlexNet (11×11 and 5×5), VGG uses only small **3×3 convolution filters**, stacking many of them to build a much deeper network. This approach reduces the number of parameters per convolution while increasing the network's ability to learn complex visual features.

VGG-16, for example, contains **13 convolutional layers** followed by **3 fully connected layers**. As the image passes through the network, the spatial resolution gradually decreases while the number of feature maps increases. Early layers learn simple features such as edges and textures, whereas deeper layers capture object parts and complete objects.

VGG achieved one of the best performances on ImageNet and became one of the most influential CNN backbones. Its simple and consistent design made it a popular backbone for many computer vision tasks and transfer learning applications.

However, this simplicity comes with a trade-off. VGG contains around **138 million parameters**, making it computationally expensive and memory-intensive. Although it improved accuracy over AlexNet, later architectures such as Inception and ResNet achieved similar or better performance while being significantly more efficient.

---

**Official paper :** [Here](https://arxiv.org/abs/1409.1556)
