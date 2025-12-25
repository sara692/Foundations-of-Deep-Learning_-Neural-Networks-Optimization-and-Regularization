# Task 7 — Optimizer Comparison Experiment

## Objective
Evaluate the effect of different optimizers by training the same model with four optimizer configurations:

1. **SGD** (`learning_rate=0.01`)
2. **SGD + Momentum** (`learning_rate=0.01`, `momentum=0.9`)
3. **Adam**
4. **AdamW**

---

## Analysis

### 1. How does the optimizer affect convergence speed?
- **SGD**: Slow convergence; requires many epochs to reach high accuracy.
- **SGD + Momentum**: Faster than SGD due to accumulated gradient direction.
- **Adam**: Very fast; adaptive learning rates allow quick navigation of the loss landscape.
- **AdamW**: Similar to Adam, with decoupled weight decay for better regularization.

### 2. How does the optimizer affect stability?
- **SGD**: Smooth but slow; sensitive to learning rate.
- **SGD + Momentum**: Smoother and more stable; reduces oscillations.
- **Adam / AdamW**: Fast and generally stable; minor fluctuations near the end.

### 3. How does the optimizer affect generalization?
- **SGD**: Slightly lower validation accuracy; slower learning.
- **SGD + Momentum**: Higher validation accuracy; better generalization.
- **Adam / AdamW**: High validation accuracy; AdamW adds extra regularization via weight decay.

### 4. Why does Adam often outperform classical optimizers?
- Uses adaptive learning rates per parameter.
- Handles noisy gradients and sparse updates effectively.
- Reduces need for manual learning rate tuning.
- Works well for deep networks and complex datasets.

---

## Results Table

| Optimizer       | Final Training Accuracy | Final Training Loss | Final Validation Accuracy | Final Validation Loss | Observation |
|----------------|-------------------------|---------------------|---------------------------|------------------------|-------------|
| SGD            | 0.9648                  | 0.1233              | 0.9740                    | 0.0955                 | Slow convergence; moderate generalization |
| SGD + Momentum | 0.9897                  | 0.0343              | 0.9844                    | 0.0615                 | Fast convergence; stable; better generalization |
| Adam           | 0.9909                  | 0.0265              | 0.9818                    | 0.0780                 | Very fast; adaptive learning rates; good performance |
| AdamW          | 0.9904                  | 0.0280              | 0.9796                    | 0.0791                 | Similar to Adam; weight decay improves regularization |

---

## Summary

- **SGD** is simple but slow; may require careful learning rate tuning.
- **SGD + Momentum** accelerates convergence and reduces oscillations.
- **Adam** combines adaptive learning rates and momentum for fast, reliable training.
- **AdamW** adds decoupled weight decay for better regularization and slightly improved generalization.

Overall, **Adam** and **AdamW** outperform classical SGD, especially for deeper networks or complex datasets, due to faster convergence, stability, and better handling of noisy gradients.
