# Task 9 — Activation Function Swap (ReLU vs Tanh vs Softsign vs GELU)

## Objective
Evaluate the effect of different activation functions on training dynamics, gradient flow, and generalization by training the same model while keeping the model architecture, optimizer (Adam), learning rate, batch size (32), and EarlyStopping configuration fixed.

The evaluated activations are:
- **ReLU**
- **Tanh**
- **Softsign**
- **GELU**

---

## Analysis

### 1. How does activation affect gradient flow?
- **ReLU**: Strong and stable gradient flow for positive inputs. Fast convergence with minimal vanishing gradient issues. Some neurons may "die" but Adam mitigates this.
- **Tanh**: Gradients shrink near saturation (-1, 1), causing slower convergence. Zero-centered output improves symmetry but gradient flow weakens in deeper layers.
- **Softsign**: Similar to tanh but saturates more gradually. Gradient decay is smoother but still weaker than ReLU or GELU.
- **GELU**: Smooth, probabilistic gating preserves gradient flow. Avoids hard zeroing and allows rich gradient information, helping fast convergence and stable optimization.

### 2. Which activations risk vanishing gradients?
- **High Risk**: Tanh (saturates quickly)
- **Moderate Risk**: Softsign (bounded output but smoother)
- **Low Risk**: GELU (smooth, non-saturating)
- **Very Low Risk**: ReLU (linear for positive inputs)

### 3. Why does GELU perform well in deep architectures like Transformers?
- Smoothly gates inputs, allowing small negative values to contribute rather than zeroing them.
- Produces stable and expressive gradients that pair well with Adam and residual connections.
- Enhances generalization in very deep networks by avoiding sharp saturation regions.

### 4. Why is ReLU still preferred for many MLP and CNN models?
- Computationally simple and efficient.
- Strong gradient propagation enables fast convergence.
- Minimal tuning required; works well with both shallow and moderately deep networks.
- Achieves performance comparable to GELU in many standard tasks.

---

## Results Table

| Activation | Best Epoch | Final Training Accuracy | Final Training Loss | Final Validation Accuracy | Final Validation Loss | Observation |
|------------|------------|-------------------------|---------------------|---------------------------|------------------------|-------------|
| ReLU       | 10         | 0.9901                  | 0.0295              | 0.9826                    | 0.0671                 | Fast convergence; very stable; reliable default |
| Tanh       | 12         | 0.9911                  | 0.0288              | 0.9804                    | 0.0719                 | Slower convergence; weaker gradient flow; moderate generalization |
| Softsign   | 15         | 0.9883                  | 0.0359              | 0.9808                    | 0.0716                 | Smooth but slow; requires more epochs; moderate generalization |
| GELU       | 9          | 0.9903                  | 0.0283              | 0.9828                    | 0.0705                 | Fastest convergence; smooth gradient flow; highest generalization |

---

## Summary
- Activation function strongly influences gradient flow, convergence speed, and generalization.
- **ReLU** remains efficient and reliable for MLP and CNN tasks.
- **Tanh** and **Softsign** are slower and more prone to gradient saturation.
- **GELU** combines smooth gating and strong gradient preservation, leading to fast convergence and superior performance, especially in deeper architectures.

Overall, **GELU** and **ReLU** provide the best combination of stability and accuracy under Adam optimization.
