# AlexNet (Krizhevsky, Sutskever, Hinton 2012)

![AlexNet Architecture](/assets/architectures/cnn/alexnet_architecture.png)


## 1. Problem it solves
LeNet-5 was too shallow and narrow, designed only for small grayscale
images, and had way too little capacity to represent complex, high-resolution
RGB images. AlexNet comes to solve exactly that: it needs a much deeper
architecture to properly represent complex real-world images.

## 2. Main idea
Combine computational power (GPUs), a deep architecture, and regularization
techniques to make deep learning feasible and effective on large-scale,
complex RGB image classification (ImageNet).

## 3. How it works
- 5 convolutional layers and 3 fully connected layers (with ReLU after each learnable layer except the output).

- The network is split into two parallel "columns," each running on a
  separate GPU, except for the last layer a hardware necessity of the
  time, not a purely architectural choice.
- Uses the ReLU activation function, which performed better than tanh and
  sigmoid (faster training, better gradient flow).

## 4. Trade-off
AlexNet is deep and has a huge number of parameters, which allows it to
represent RGB and complex images far better than LeNet but this comes at
the cost of very high computational demand. Even though GPUs could support
this load, it remains very resource-hungry

## 5. Limitation
- Being this deep and parameter-heavy means it requires significant compute
  power, which is already problematic for real-time applications with tight
  resource constraints.
- The architecture is fairly coarse/crude, without the more systematic
  connection patterns later architectures would introduce.

## 6. Kept vs. abandoned later
- **Kept:** ReLU activation, dropout for regularization, the general idea of
  going deeper to handle complex images.
- **Abandoned:** the dual-GPU split architecture (no longer a constraint once
  hardware improved), Local Response Normalization (LRN, later dropped as
  not very useful), and the somewhat ad hoc/coarse connection patterns
  later architectures moved toward more systematic and uniform designs.

## 7. Can I explain it in 2 minutes without notes?

AlexNet can be seen as an evolution of LeNet to solve a much more complex computer vision problem. While LeNet was designed mainly for small grayscale images like handwritten digits, AlexNet was designed to handle large RGB images from ImageNet, with millions of parameters and thousands of object categories.

One of the major contributions of AlexNet was showing that the combination of deep CNNs, GPU acceleration, massive data, regularisation techniques could significantly improve image classification performance. This result was a turning point that accelerated the deep learning revolution in computer vision.

The main challenge was that increasing the complexity of images also increased the computational cost. AlexNet addressed this by introducing a much deeper architecture with more convolutional layers, more filters, and larger input images (227×227×3). As a result, it achieved significantly better performance than LeNet, but at the cost of requiring powerful GPUs, large-scale datasets, and more advanced training techniques. This highlights the trade-off between accuracy and computational efficiency: while LeNet is lightweight and suitable for simple tasks, AlexNet is far more powerful but substantially more computationally expensive and difficult to train.

---

[Official paper available] : [Here](https://proceedings.neurips.cc/paper_files/paper/2012/file/c399862d3b9d6b76c8436e924a68c45b-Paper.pdf)