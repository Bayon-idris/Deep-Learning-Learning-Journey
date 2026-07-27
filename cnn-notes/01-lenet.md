# LeNet-5 (LeCun et al., 1998) 

![LeNet-5 Architecture](/assets/architectures/cnn/lenet5_architecture.png) 

## 1. Problem it solves
Before LeNet-5, vision systems relied on hand-crafted features (edges, shapes,
textures designed manually by engineers). LeNet-5 showed that a network could
learn useful visual features directly from raw pixels, applied to handwritten
digit recognition (e.g. bank checks).

## 2. Main idea
Stack `conv → pool → conv → pool → FC` layers so the network learns a
hierarchy of features on its own: low-level edges → mid-level shapes →
high-level digit representations instead of relying on manually designed
features.

## 3. How it works
- Convolutions with shared weights scan the image locally. Compared to a
  fully-connected network applied directly to raw pixels, this drastically
  cuts the number of parameters while preserving spatial structure.
- Average pooling (2x2) downsamples between the two convolutional layers.
- Uses tanh/sigmoid activations  ReLU wasn't in practical use yet.
- Around 60k trainable parameters, designed for 32x32 grayscale input only.

## 4. Trade-off
Extremely lightweight and fast to train/run (even on 1990s hardware) in
exchange for very low representational capacity.

## 5. Limitation
- Too shallow to handle complex objects, large datasets, or high-resolution
  images.

- Designed primarily for small grayscale images such as handwritten digits, with limited applicability to complex RGB images.

- Missing modern techniques (BatchNorm, Dropout, ReLU, data augmentation) →
  more prone to overfitting and unstable training on harder datasets.

## 6. Kept vs. abandoned later
- **Kept:** the conv→pool→conv→pool→FC pattern, weight sharing, and the idea
  of hierarchical automatic feature learning this became the backbone
  pattern for essentially every CNN since.
- **Abandoned:** tanh/sigmoid (→ ReLU), average pooling (→ max pooling in
  most later architectures), shallow depth (→ much deeper networks enabled
  by better activations, regularization, and hardware).

## 7. Can I explain it in 2 minutes without notes?

Yann LeCun was a pioneer of convolutional neural networks (CNNs), notably with LeNet-5 in 1998. His key idea was to let the network automatically learn important image representations directly from raw pixels, rather than relying solely on features manually designed by engineers.

Before CNNs, many vision systems used approaches based on hand-crafted features, such as edge, shape, or texture detection. The problem was that these features required significant human expertise and could be limited in scope.
This approach laid a fundamental foundation for modern computer vision and was subsequently expanded upon with the advent of deep learning and large amounts of data.

So, LeNet introduced the idea of automatic feature extraction from pixels, but it was limited by the hardware and datasets available at that time. It was mainly designed for small grayscale images. AlexNet extended this idea to real-world images by increasing depth, capacity, and computational resources.

---

[Official paper available] : [Here](https://ieeexplore.ieee.org/document/726791)