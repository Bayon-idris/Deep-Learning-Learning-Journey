# EfficientNet (Tan & Le, 2019)

![EfficientNet Architecture](/assets/architectures/cnn/efficientnet_architecture.webp) 

## 1. Problem it solves

Previous CNN architectures such as **ResNet** and **MobileNet** improved either **accuracy** or **efficiency**, but scaling them was largely a manual process. Developers typically increased the network's **depth**, **width**, or **input resolution** independently, relying on trial and error to find a good balance.

EfficientNet asks a simple question:

**Can we scale a CNN in a systematic way that maximizes both accuracy and efficiency for a given computational budget?**

---

## 2. Main idea

The key innovation of EfficientNet is **Compound Scaling**.

Instead of increasing only the network's **depth**, **width**, or **input resolution**, EfficientNet scales **all three dimensions simultaneously** using a carefully designed scaling strategy.

This balanced approach allows the network to make better use of additional computational resources, producing a family of models (**EfficientNet-B0** to **EfficientNet-B7**) that offer different trade-offs between speed and accuracy.

Another important component is the **MBConv (Mobile Inverted Bottleneck Convolution)** block, inherited from MobileNetV2 and enhanced with **Squeeze-and-Excitation (SE)** modules to improve feature representation.

---

## 3. How it works

* Input image size varies depending on the model (**224×224** for B0 up to **600×600** for B7).
* EfficientNet is built using **MBConv blocks**, which combine:

  * **Depthwise Separable Convolutions** for computational efficiency.
  * **Inverted Residual Connections** inherited from MobileNetV2.
  * **Squeeze-and-Excitation (SE) blocks**, which allow the network to emphasize the most informative feature channels.
* The network ends with **Global Average Pooling**, a fully connected layer, and a Softmax classifier.

Rather than redesigning the architecture for every model size, EfficientNet simply applies **Compound Scaling**, increasing **depth**, **width**, and **resolution** together in a balanced manner.

---

## 4. Trade-off

EfficientNet achieves an excellent balance between **accuracy** and **computational efficiency**. For the same computational budget, it generally outperforms previous CNN architectures such as ResNet and MobileNet.

The EfficientNet family ranges from the lightweight **EfficientNet-B0** (**≈5.3 million parameters**) to the much larger **EfficientNet-B7** (**≈66 million parameters**), allowing developers to choose the most appropriate model for their hardware.

The trade-off is that EfficientNet relies on a more sophisticated architecture, combining several techniques such as **MBConv**, **Depthwise Separable Convolutions**, **Squeeze-and-Excitation**, and **Compound Scaling**, making it more complex than earlier CNN designs.

---

## 5. Limitation

* EfficientNet remains a **convolutional neural network**, making it less effective than Vision Transformers at modeling long-range relationships.
* Larger EfficientNet variants become computationally demanding despite their excellent efficiency.
* The architecture is more complex than previous CNNs, making implementation and customization more challenging.
* Compound Scaling was primarily optimized for image classification and may require adaptation for other computer vision tasks.

---

## 6. Kept vs. abandoned later

* **Kept:** **Compound Scaling**, **MBConv blocks**, **Depthwise Separable Convolutions**, **Squeeze-and-Excitation modules**, and the philosophy of maximizing accuracy per computational cost. These ideas continue to influence modern efficient CNN architectures, including **EfficientNetV2**.

* **Abandoned:** later computer vision research increasingly shifted toward **Vision Transformers**, which replace many convolutional operations with self-attention. While EfficientNet remains highly competitive, purely convolutional architectures are no longer the dominant research direction for many large-scale vision tasks.

---

## 7. Can I explain it in 2 minutes without notes?

After MobileNet demonstrated that CNNs could become lightweight enough for mobile devices, researchers faced another challenge: **how can we improve both accuracy and efficiency without manually redesigning every new model?** This question led to EfficientNet, introduced by Google in 2019.

The main innovation of EfficientNet is **Compound Scaling**. Instead of increasing only one aspect of a CNN—such as its depth, width, or input resolution—EfficientNet scales **all three dimensions together** in a balanced way. This allows every additional computational resource to be used more effectively.

EfficientNet is built on **MBConv blocks**, inherited from MobileNetV2, which combine **Depthwise Separable Convolutions**, **Inverted Residual Connections**, and **Squeeze-and-Excitation (SE) modules**. These components enable the network to remain lightweight while improving feature representation.

Rather than designing a different architecture for each application, EfficientNet provides a family of models ranging from **EfficientNet-B0 (≈5.3 million parameters)** to **EfficientNet-B7 (≈66 million parameters)**, allowing developers to choose the best balance between speed and accuracy.

EfficientNet became one of the most influential CNN architectures because it demonstrated that **carefully balancing depth, width, and resolution is more effective than scaling only one dimension**. Although Vision Transformers have since become increasingly popular, EfficientNet remains one of the strongest and most efficient convolutional neural network families for image classification and transfer learning.

---

**Official paper:** https://arxiv.org/abs/1905.11946
