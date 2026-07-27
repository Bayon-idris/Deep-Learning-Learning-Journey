# Deep Learning Implementations

A collection of machine learning and deep learning models implemented to understand the mathematics and training mechanisms behind modern AI systems.

The goal is not to create production-ready models or achieve state-of-the-art performance.

Instead, each notebook focuses on understanding how these algorithms work internally through implementation and experimentation.

---

# Project Goals

This section focuses on implementation:

- Forward propagation
- Backpropagation
- Gradient descent
- Loss functions
- Parameter optimization
- Neural network training
- CNN training workflows


---

# Notebook Progress

| Notebook | Approach | Status |
|---|---|---|
| 01 - Single Layer Perceptron | NumPy from scratch | ✅ Completed |
| 02 - Logistic Regression | NumPy from scratch | ✅ Completed |
| 03 - Neural Network One Hidden Layer | NumPy from scratch | ✅ Completed |
| 04 - Deep Neural Network (L Layers) | NumPy from scratch | ✅ Completed |
| 05 - Convolution Operations | NumPy from scratch | ✅ Completed |
| 06 - Convolutional Neural Network | TensorFlow/Keras | ✅ Completed |
| 07 - Recurrent Neural Networks | TensorFlow/Keras | Planned |


# From Scratch Implementations

Notebooks 01-05 implement the main operations manually using NumPy:

- Forward pass
- Backward pass
- Gradient calculation
- Parameter updates


The objective is to understand the mathematical foundations before using high-level deep learning frameworks.


---

# CNN Experiments

From notebook 06 onward, the focus shifts from reimplementing every operation manually toward building and training practical deep learning models.

TensorFlow/Keras is used because the objective becomes understanding:

- CNN architecture design
- Training pipelines
- Dataset handling
- Model evaluation


---

# Key Observation

A fully connected neural network is not naturally suited for image tasks because it ignores spatial relationships between pixels.

CNNs solve this problem by learning local visual patterns through convolution operations.

This repository demonstrates this difference experimentally:

- Fully connected networks achieve limited performance on image classification tasks.
- CNNs significantly improve performance by learning hierarchical visual features.
