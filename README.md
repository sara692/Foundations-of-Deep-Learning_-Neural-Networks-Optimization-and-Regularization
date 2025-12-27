# Foundations-of-Deep-Learning_-Neural-Networks-Optimization-and-Regularization
# Deep Learning & Neural Networks — MNIST Practical

## Project Overview
This repository contains a comprehensive practical exploration of neural networks using the MNIST dataset. The project focuses on building, training, and analyzing fully connected neural networks while introducing key deep learning concepts such as regularization, optimization, activation functions, batch effects, and model capacity.

The work is divided into two main sections, each covering theoretical and practical aspects of neural networks with hands-on experiments.

---

## Section 1 — Practical Part #1: Building & Training a Neural Network
**Objectives Covered:**
- Loading and preprocessing the MNIST dataset.
- Flattening image data for fully connected networks.
- Building a simple neural network:
  - Input layer (Flatten)
  - Hidden Dense layer (ReLU activation)
  - Output layer (Softmax activation)
- Compiling the model using the Adam optimizer.
- Training the model and monitoring training/validation loss.
- Predicting and visualizing test samples.

**Learning Outcome:**  
Students gain a practical understanding of how forward and backward passes operate within a simple neural network.

---

## Section 2 — Practical Part #2: Data Splitting, Regularization & Early Stopping
**Key Concepts Introduced:**

1. **Proper Dataset Splitting**  
   - Training set: For learning.  
   - Validation set: For tuning hyperparameters and preventing overfitting.  
   - Test set: For final unbiased performance evaluation.  
   *Important:* Never use the test set as a validation set, as it biases the evaluation.

2. **Regularization Techniques**  
   - Dropout layers to reduce overfitting.  
   - EarlyStopping to detect convergence and stop training automatically.

3. **Improved Model Pipeline**  
   - Training over multiple epochs.  
   - Monitoring training vs. validation performance.  
   - Evaluating on the final test set.  
   - Predicting and analyzing results.

**Learning Outcome:**  
Students understand how model generalization is improved using proper data splitting, dropout, and EarlyStopping.

---

## Part 1 — Core Model Understanding & Prediction Behavior

### Task 1 — Deep Prediction Analysis
- Run `model.predict()` on selected test samples.
- Compare predicted vs. true labels.
- Analyze how forward pass, activations (ReLU, Softmax), and Adam optimizer affected predictions.

### Task 2 — Custom Image Generalization Test
- Create a handwritten digit, preprocess (grayscale, 28×28 resize, normalization), and predict.
- Analyze correct/incorrect classifications.
- Discuss distribution shift and representation learning effects.

### Task 3 — Epoch-Based Learning Curve Exploration
- Train models with 5, 10, and 20 epochs.
- Plot `loss vs val_loss` and `accuracy vs val_accuracy`.
- Analyze overfitting signs and convergence behavior under Adam optimizer.

### Task 4 — EarlyStopping Behavior Analysis
- Use `EarlyStopping(patience=3, restore_best_weights=True)`.
- Analyze when training stopped and the role of validation loss.
- Discuss impact of patience changes and optimizer differences.

---

## Part 2 — Regularization & Optimization Mastery

### Task 5 — Dropout Ablation Study
- Test three configurations: No Dropout, Dropout=0.1, Dropout=0.3.
- Compare training vs. validation loss and overfitting levels.
- Explain how Dropout encourages robust representations.

### Task 6 — L2 Regularization Experiment
- Apply `kernel_regularizer=keras.regularizers.l2()` with values 0.0001, 0.001, 0.01.
- Analyze weight magnitude reduction, generalization improvement, and validation loss trends.

### Task 7 — Optimizer Comparison Challenge
- Compare optimizers: SGD, SGD+Momentum, Adam, AdamW.
- Plot loss and accuracy curves.
- Discuss convergence speed, stability, and why Adam often outperforms classical optimizers.

### Task 8 — Batch Size & Gradient Noise Experiment
- Train models with batch sizes 8, 32, 128.
- Analyze gradient noise effects, convergence speed, and generalization.

### Task 9 — Activation Function Swap
- Replace ReLU with Tanh, Softsign, GELU.
- Analyze gradient flow, vanishing gradient risks, and performance differences.

### Task 10 — Weight Inspection & Model Capacity Analysis
- Extract first Dense layer weights: `w, b = model.layers[1].get_weights()`.
- Analyze parameter count, overfitting risks, and the role of Dropout, L2, and EarlyStopping in mitigating overfitting.

---

## Repository Structure
project/
├── notebook.ipynb                    # Main Jupyter notebook with implementation
├── README.md                         # Project overview (this file)
├── results/                          # Outputs from experiments
│   ├── predictions/                  # Prediction visualizations
│   ├── loss_curves/                  # Training/validation loss plots
│   └── optimizer_tests/              # Optimizer comparison results
└── submission/                       # Documentation of experiments
    ├── Task01_PredictionAnalysis.md  # Analysis of model predictions
    ├── Task02_CustomDigit.md         # Custom digit classification results
    ├── Task03_Epochs.md              # Effect of training epochs
    ├── Task04_EarlyStopping.md       # Early stopping implementation
    ├── Task05_Dropout.md             # Dropout regularization study
    ├── Task06_L2.md                  # L2 regularization analysis
    ├── Task07_Optimizers.md          # Optimizer comparison
    ├── Task08_BatchSize.md           # Batch size impact study
    ├── Task09_Activations.md         # Activation function comparison
    └── Task10_Weights.md             # Weight initialization analysis
    
---

## Sample Results

- **Training vs. Validation Loss Curves**  
  Visualizations of loss and accuracy over different numbers of epochs, showing learning dynamics and overfitting trends.

- **Optimizer Comparison Plots**  
  Curves comparing convergence speed and stability of different optimizers: SGD, SGD+Momentum, Adam, and AdamW.

- **Predicted Labels**  
  Predictions on MNIST test samples and custom handwritten digits, highlighting correct and incorrect classifications.

- **Regularization Analysis**  
  Effects of Dropout and L2 regularization on model generalization and prevention of overfitting.

---

## Key Takeaways

- Neural network predictions depend on **forward pass transformations**, **activation functions**, and **optimization dynamics**.  
- Proper **data splitting**, **Dropout**, and **EarlyStopping** significantly improve model generalization.  
- Hyperparameters such as **batch size**, **learning rate**, and **activation functions** greatly influence training stability and convergence.

