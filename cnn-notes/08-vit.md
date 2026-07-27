# Vision Transformer (ViT) (Dosovitskiy et al., 2020)

![ViT Architecture](/assets/architectures/cnn/vit_architecture.png)

## 1. Problem it solves

Most previous mainstream vision architectures from LeNet to EfficientNet were primarily based on convolutions. , which naturally focus on local regions of an image. Although CNNs become increasingly powerful as they grow deeper, modeling long-range relationships between distant image regions still requires many stacked layers.

Vision Transformer asks a completely different question:

**Can we replace convolutions entirely and process an image using the same Transformer architecture that revolutionized Natural Language Processing?**

---

## 2. Main idea

The key innovation of Vision Transformer is to treat an image as a **sequence of image patches**, just as a sentence is treated as a sequence of words in NLP.

Instead of applying convolutional filters, the image is divided into fixed-size patches. Each patch is converted into an embedding and processed by a standard **Transformer Encoder**, where **Self-Attention** allows every patch to interact directly with every other patch in the image.

This gives the model a **global receptive field from the very first layer**, unlike CNNs, which gradually build global understanding through many convolutional layers.

---

## 3. How it works

* Input image size: typically **224 × 224 × 3**.
* The image is divided into fixed-size patches (for example **16 × 16**), producing a sequence of image tokens.
* Each patch is converted into a vector called a **Patch Embedding**.
* A **Positional Embedding** is added so the model knows where each patch is located in the image.
* The sequence is processed by multiple **Transformer Encoder** blocks composed of:

  * **Multi-Head Self-Attention**
  * **Feed-Forward Networks (MLPs)**
  * **Residual Connections**
  * **Layer Normalization**
* A special **[CLS] token** collects information from all patches and is used for the final image classification.

Unlike CNNs, every image patch can communicate directly with every other patch through **Self-Attention**, allowing the model to capture global relationships immediately.

---

## 4. Trade-off

Vision Transformer achieves state-of-the-art performance when trained on very large datasets, thanks to its ability to model global relationships across the entire image.

The standard **ViT-Base** model contains approximately **86 million parameters**, making it comparable to large CNNs such as VGG while providing significantly stronger performance when sufficient training data is available.

The trade-off is that Vision Transformers require **much larger datasets** and more computational resources than CNNs. They also have higher computational costs because **Self-Attention** compares every image patch with every other patch.

---

## 5. Limitation

* Vision Transformers generally require **large-scale pretraining** to outperform CNNs.
* **Self-Attention** becomes computationally expensive for high-resolution images.
* The original ViT does not naturally build multi-scale feature representations like CNNs.
* Training Vision Transformers is typically more resource-intensive than training traditional convolutional networks.

---

## 6. Kept vs. abandoned later

* **Kept:** **Patch Embedding**, **Self-Attention**, **Transformer Encoder blocks**, **Residual Connections**, and the overall Transformer philosophy have become the foundation of many modern computer vision models, including **DeiT**, **Swin Transformer**, **BEiT**, and numerous multimodal architectures.

* **Abandoned:** the original Vision Transformer processes all image patches globally at every layer, making computation expensive. Later architectures such as **Swin Transformer** introduced **Window-based Self-Attention** and hierarchical feature representations to improve scalability while preserving the advantages of Transformers.

---

## 7. Can I explain it in 2 minutes without notes?

After EfficientNet demonstrated how far convolutional neural networks could be optimized, researchers began asking an even more radical question: **do we still need convolutions at all?** Inspired by the success of Transformers in Natural Language Processing, Google introduced the **Vision Transformer (ViT)** in 2020.

The main idea of ViT is to treat an image as a sequence of **small image patches**, just as a sentence is treated as a sequence of words. Each patch is converted into an embedding and processed by a standard **Transformer Encoder** using **Self-Attention**.

Unlike CNNs, where information spreads gradually through stacked convolutional layers, Self-Attention allows every image patch to communicate directly with every other patch from the very first layer. This gives the model a global understanding of the image much earlier in the computation.

The standard **ViT-Base** model contains approximately **86 million parameters** and achieved state-of-the-art image classification performance when trained on very large datasets. However, this impressive performance comes with higher computational requirements and a strong dependence on large-scale pretraining.

Vision Transformer marked a major turning point in computer vision by demonstrating that **Transformers could successfully replace convolutions for image understanding**. Its core ideas now form the foundation of many modern vision models, including **Swin Transformer**, **DeiT**, and numerous multimodal AI systems.

---

**Official paper:** https://arxiv.org/abs/2010.11929
