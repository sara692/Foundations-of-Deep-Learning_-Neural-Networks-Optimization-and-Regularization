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
