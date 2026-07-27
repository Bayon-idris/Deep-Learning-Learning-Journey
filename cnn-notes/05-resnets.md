# ResNet (He et al., 2015)

![ResNet Architecture](/assets/architectures/cnn/resnet_architecture.png)

## 1. Problem it solves

VGG and GoogLeNet demonstrated that increasing the depth of a CNN generally improves accuracy. However, researchers discovered that simply stacking more layers eventually makes the network **harder to train**. Surprisingly, deeper networks can suffer from degradation, where optimization becomes harder and training accuracy worsens even without overfitting, not because of overfitting, but because optimization becomes increasingly difficult.

ResNet addresses a simple but fundamental question:

**How can we train very deep neural networks (50, 101, or even 152 layers) without suffering from this degradation problem?**


## 2. Main idea

The key innovation of ResNet is **Residual Learning**.

Instead of forcing each block to learn an entirely new transformation, the network learns only the **residual** (the difference between the input and the desired output). This is achieved through **skip connections** (also called **identity shortcuts**) that directly add the input of a block to its output.

These shortcut connections make it much easier for gradients to flow through the network during backpropagation, allowing extremely deep CNNs to be trained successfully.


## 3. How it works

* Input image size: **224 × 224 × 3**.
* The network begins with a standard convolution and max-pooling layer.
* It then stacks multiple **Residual Blocks** organized into four stages.
* Each residual block contains a few convolutional layers together with a **skip connection** that bypasses them.
* Depending on the model, ResNet uses either:

  * **Basic Blocks** (ResNet-18 and ResNet-34).
  * **Bottleneck Blocks** (ResNet-50, ResNet-101, and ResNet-152), which use a **1×1 → 3×3 → 1×1** design to reduce computation.
* The network finishes with **Global Average Pooling**, a fully connected layer, and a Softmax classifier.

The shortcut connection provides a direct path for both the information and the gradients, making optimization significantly easier as the network becomes deeper.


## 4. Trade-off

ResNet allows networks to become **much deeper** while remaining relatively easy to optimize. For example, **ResNet-50** contains approximately **25.6 million parameters**, far fewer than **VGG-16's 138 million**, while achieving better accuracy.

The main trade-off is that deeper ResNet variants require more computation than lightweight models such as MobileNet. Although the shortcut connections themselves add very little computational cost, increasing the number of residual blocks naturally increases training and inference time.


## 5. Limitation

* Very deep versions such as **ResNet-101** and **ResNet-152** remain computationally expensive.
* Each residual block only combines its output with the previous input, limiting feature reuse compared with later architectures such as DenseNet.
* The network still relies entirely on convolutional operations, making it less effective at modeling long-range relationships than later attention-based architectures such as Vision Transformers.
* Choosing the depth of the network remains a manual design decision.

## 6. Kept vs. abandoned later

* **Kept:** **Residual (skip) connections**, **bottleneck blocks**, **Global Average Pooling**, and the overall philosophy of building very deep networks. Residual connections became one of the most influential ideas in deep learning and are still widely used in modern CNNs and even Transformer architectures.

* **Abandoned:** simply increasing the number of residual blocks is no longer considered the best scaling strategy. Later architectures such as **DenseNet** improved feature reuse, **EfficientNet** introduced compound scaling, and **Vision Transformers** replaced many convolutional operations with self-attention mechanisms.


## 7. Can I explain it in 2 minutes without notes?

After GoogLeNet demonstrated that CNNs could become both deep and computationally efficient, researchers naturally wondered whether making networks even deeper would continue improving performance. Surprisingly, the answer was no. Beyond a certain depth, training became more difficult, and deeper networks often performed worse than shallower ones.

ResNet, introduced by Microsoft Research in 2015, solved this problem with one simple but revolutionary idea: **skip connections**. Instead of forcing every layer to learn a completely new representation, each residual block learns only the difference between its input and output, while the original input is passed directly through the shortcut connection.

These shortcuts make it much easier for gradients to flow during backpropagation, allowing networks with **50, 101, or even 152 layers** to train successfully. As a result, ResNet achieved state-of-the-art ImageNet performance while remaining much more parameter-efficient than VGG, with **about 25.6 million parameters** for ResNet-50 compared with **approximately 138 million** for VGG-16.

ResNet quickly became one of the most influential architectures in computer vision. Its residual learning principle is still widely used today, not only in modern CNNs but also in Transformer models. However, although residual connections solved the optimization problem of very deep networks, later architectures such as DenseNet and EfficientNet explored new ways to improve feature reuse and computational efficiency.

---

**Official paper:** https://arxiv.org/abs/1512.03385
