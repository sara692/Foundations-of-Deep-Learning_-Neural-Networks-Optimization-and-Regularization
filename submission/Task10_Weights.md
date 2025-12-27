# Task 10 — Weight Inspection & Model Capacity Analysis

## Objective
Analyze the capacity of a fully connected neural network by inspecting the weights of the first Dense layer. Discuss how the number of parameters affects overfitting and how regularization techniques mitigate this risk.

The evaluated model uses:  
- **Optimizer:** Adam  
- **Batch size:** 32  
- **EarlyStopping:** patience=3, restore_best_weights=True  
- **Dropout:** 0.1  

---

## Code

```python
# Extract weights from the first Dense layer
w, b = model.layers[1].get_weights()

# Inspect shape of weights
print("Weights shape:", w.shape)
print("Bias shape:", b.shape)
```
# Task 10 — Weight Inspection & Model Capacity Analysis

## Analysis

### 1. Why is the number of parameters so large?
- Input features = 28 × 28 = 784  
- Dense layer neurons = 128  
- Total weights = 784 × 128 = **100,352**  
- Total biases = 128  
- **Total parameters = 100,480**  

A fully connected layer connects every input to every neuron, creating a high parameter count.

---

### 2. How does high model capacity increase overfitting risk?
- High capacity allows the network to **memorize training data**, rather than learning general patterns.  
- Result: **low training loss** but **high validation loss**, indicating poor generalization.

---

### 3. How do regularization techniques mitigate overfitting?

| Technique       | Mechanism                                                                 | Effect on Overfitting                                  |
|-----------------|---------------------------------------------------------------------------|-------------------------------------------------------|
| **Dropout**     | Randomly deactivates neurons during training                               | Reduces co-adaptation of neurons; prevents memorization |
| **L2 Regularization** | Adds a penalty proportional to squared weights to the loss function      | Encourages smaller weights; simplifies the model     |
| **EarlyStopping** | Stops training when validation loss stops improving                        | Prevents over-training and reduces memorization      |

---

### 4. Observations
- The first Dense layer dominates the parameter count due to full connectivity.  
- Even small networks can have **tens of thousands of parameters**, making regularization essential.  
- Dropout, L2, and EarlyStopping work together to balance **model capacity** and **generalization performance**.

---

## Summary
- **Weight inspection** reveals why fully connected layers can easily overfit.  
- **High-capacity networks** require careful regularization.  
- Techniques like **Dropout, L2, and EarlyStopping** each mitigate overfitting in complementary ways.  
- Understanding parameter count helps in designing models that generalize well without unnecessary complexity.
