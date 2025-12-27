# Task 8 — Batch Size & Gradient Noise Experiment

## Objective
Evaluate the effect of batch size on training dynamics and generalization by training the same model with three different batch sizes while keeping the model architecture, optimizer (Adam), learning rate, and EarlyStopping configuration fixed.

The evaluated batch sizes are:
- **Batch Size = 8**
- **Batch Size = 32**
- **Batch Size = 128**

---

## Analysis

### 1. Why do smaller batches introduce gradient noise?
Smaller batch sizes compute gradients using fewer samples, resulting in a high-variance approximation of the true dataset gradient. This causes frequent fluctuations in gradient direction between updates, producing noisy and less smooth loss curves during training.

In this experiment, batch size 8 exhibited noticeable instability in validation loss after early epochs, which is characteristic of noisy gradient updates.

### 2. When is gradient noise beneficial?
Gradient noise is beneficial when:
- Escaping sharp or local minima
- Encouraging broader exploration of the loss surface
- Acting as implicit regularization that improves generalization

With batch size 8, the model achieved fast early learning and high validation accuracy, demonstrating how noise can accelerate learning and help avoid poor minima. However, excessive noise later led to training instability.

### 3. Why do larger batches converge slower and may generalize worse?
Larger batch sizes produce low-variance, smooth gradients, resulting in:
- Fewer weight updates per epoch
- More conservative parameter changes
- Reduced exploration of the loss landscape

In this experiment, batch size 128 required more epochs before EarlyStopping, showing slower convergence in terms of epochs. The model followed a smooth optimization path but tended to plateau earlier, indicating reduced generalization benefits compared to smaller batches.

### 4. How does batch size affect the smoothness of loss curves?
- **Batch Size = 8** → Highly noisy and fluctuating loss curves
- **Batch Size = 32** → Moderately smooth and stable curves
- **Batch Size = 128** → Very smooth and steady loss curves

This behavior directly reflects how gradient variance decreases as batch size increases.

---

## Results Table

| Batch Size | Final Training Accuracy | Final Training Loss | Final Validation Accuracy | Final Validation Loss | Observation |
|------------|------------------------|---------------------|---------------------------|------------------------|-------------|
| 8          | ~0.988                 | ~0.0367             | ~0.9794                   | ~0.0882                | Fast learning; high gradient noise; unstable validation |
| 32         | ~0.993                 | ~0.0202             | ~0.9832                   | ~0.0724                | Best balance of stability and generalization |
| 128        | ~0.992                 | ~0.0264             | ~0.9828                   | ~0.0687                | Very smooth updates; slower convergence; conservative learning |

---

## Summary
- Small batch sizes introduce gradient noise that improves exploration and acts as implicit regularization but may destabilize training.
- Large batch sizes provide smooth and stable optimization but converge more slowly in terms of epochs and may generalize worse.
- **Batch Size = 32** achieves the best trade-off between convergence speed, stability, and generalization.

Overall, batch size significantly influences optimization behavior, and moderate batch sizes tend to outperform extreme values when using adaptive optimizers such as Adam.
