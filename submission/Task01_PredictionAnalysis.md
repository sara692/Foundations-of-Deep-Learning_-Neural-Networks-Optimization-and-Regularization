# Task 1 — Deep Prediction Analysis

Provide a conceptual explanation of the result by referencing:

### How the forward pass transforms inputs through layers
The input image is **flattened to 1D** so Dense layers can process it numerically. Each layer computes **weighted sums plus bias** and applies **ReLU**, extracting meaningful features. The output layer produces **10 values** for the 10 classes, which are processed with **Softmax** to get class probabilities.

### The role of activation functions (ReLU, Softmax)
- **ReLU:** Sets negative values to zero and keeps positive values, enabling the model to learn **non-linear relationships**.  
- **Softmax:** Converts outputs to **probabilities**; the predicted class is the one with the **highest probability** (`argmax`).

### How the optimizer (Adam) may have shaped weight updates during training
**Adam** combines **momentum** and **adaptive learning rates**, updating weights via **backpropagation** for **stable and fast convergence**.

