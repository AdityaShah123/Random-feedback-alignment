# Random-feedback-alignment

## Project Overview

This project explores the development of neural networks that are compatible with hardware architectures like neuromorphic computing systems. The traditional back-propagation algorithm, while effective for training deep neural networks, faces limitations in scaling, particularly in hardware implementations. Our research focuses on feedback alignment (FA) and its variations, which provide a more biologically plausible and hardware-efficient alternative to back-propagation. We demonstrate the performance of these algorithms on popular datasets like MNIST and CIFAR10.

---

## Problem Statement

Back-propagation (BP), the most common algorithm for training neural networks, is not biologically plausible and encounters hardware scaling issues. This project investigates feedback alignment methods, which remove the need for symmetric weight updates and make error propagation local to each layer. These methods offer potential for use in neuromorphic computing, where hardware architectures are inspired by the human brain.

---

## Neuromorphic Computing

Neuromorphic computing is a non-von Neumann architecture designed to mimic the structure of the human brain. Unlike traditional systems where memory and processing are separate, neuromorphic systems integrate memory and processing units. Key features include:
- **Parallel Processing**: Neurons and synapses operate simultaneously.
- **Collocated Memory and Processing**: Data movement is minimized by integrating memory and processing.
- **Scalability**: Easily scaled by adding additional neuromorphic chips.
- **Stochasticity**: Neurons fire based on probabilistic models.

Neuromorphic computing presents a promising alternative for implementing feedback alignment algorithms, which avoid the limitations of BP.

---

## Feedback Alignment Algorithms

### 1. Feedback Alignment (FA)
Feedback alignment (FA) uses random backward weights rather than symmetric weights to update the network's parameters. This method proves effective in training neural networks without needing exact weight symmetry, making it more biologically plausible.

### 2. Direct Feedback Alignment (DFA)
DFA improves on FA by directly projecting error signals from the output layer to each hidden layer, bypassing the recursive error propagation of FA. This reduces the need for symmetric weight updates and provides better biological feasibility.

### 3. Sparse Direct Feedback Alignment (SDFA)
SDFA further optimizes DFA by using a sparse feedback matrix. This method reduces the amount of error signal communication between layers, making it more efficient for larger networks.

---

## Mathematical Formulation

Given a dataset divided into batches \((x, y)\), where \(x\) represents inputs and \(y\) the corresponding outputs, the neural network's forward and backward passes are formulated as follows:

### Forward Pass:
For a network with two hidden layers:
1. Layer 1: \( a_1 = W_1x + b_1 \), \( h_1 = f(a_1) \)
2. Layer 2: \( a_2 = W_2h_1 + b_2 \), \( h_2 = f(a_2) \)
3. Output Layer: \( a_y = W_3h_2 + b_3 \), \( \hat{y} = f_y(a_y) \)

### Loss Function:
The cross-entropy loss function is used for output layers:
\[
L = -\frac{1}{N} \sum (y_{mn} \log(\hat{y}_{mn}) + (1 - y_{mn}) \log(1 - \hat{y}_{mn}))
\]

### Backward Pass:
Using BP, FA, and DFA, gradients are calculated for weight updates. In FA and DFA, fixed random matrices replace the weight matrices for backward propagation.

---

## Experimental Results

We conducted experiments using Artificial Neural Networks (ANNs) and Convolutional Neural Networks (CNNs) on the MNIST and CIFAR10 datasets:

### MNIST Dataset (ANN 1x800 tanh):
- **Training Accuracy (BP)**: 97.48%
- **Training Accuracy (DFA)**: 95.00%
- **Test Accuracy (BP)**: 92.10%
- **Test Accuracy (DFA)**: 92.46%

### CIFAR10 Dataset (CNN):
- **Training Accuracy (BP)**: 99.12%
- **Training Accuracy (DFA)**: 99.38%
- **Test Accuracy (BP)**: 73.53%
- **Test Accuracy (DFA)**: 79.97%

The results demonstrate that DFA performs similarly to BP, with slight improvements in test accuracy.

---

## Conclusion

Feedback alignment methods, particularly DFA and SDFA, present viable alternatives to back-propagation, especially for hardware implementation. These methods offer reduced data movement and memory access, making them well-suited for neuromorphic computing architectures. Our experiments show that these algorithms perform comparably to traditional BP methods while offering significant hardware advantages.

---
