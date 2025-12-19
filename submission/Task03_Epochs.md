# Task 3 — Epoch-Based Learning Curve Exploration

Train the model with 5, 10, and 20 epochs. For each run, analyze the loss and accuracy curves.

---

### Questions and Analysis

**Plot loss vs. val_loss and accuracy vs. val_accuracy**  
- Loss Curves: Training loss decreases steadily, while validation loss may plateau or increase after a certain point.  
- Accuracy Curves: Training accuracy continues to rise, but validation accuracy stabilizes or drops slightly in some cases.

**Identify signs of overfitting**  
- Training loss keeps decreasing while validation loss stops improving or rises.  
- Training accuracy improves, but validation accuracy plateaus or decreases.  
- These patterns indicate the model is fitting the training data too closely and not generalizing well.

**Explain how the optimizer (Adam) influenced the speed and stability of convergence**  
- Momentum: Accelerates convergence along consistent gradient directions and reduces oscillations.  
- Adaptive learning rates: Adjusts per-parameter learning rates based on past gradients, stabilizing training and allowing faster convergence.  
- Overall, Adam enables the model to train efficiently while maintaining stability.

**Conclusion**  
By comparing the curves for 5, 10, and 20 epochs, we can see the trade-off between underfitting (too few epochs) and potential overfitting (too many epochs). Adam helps ensure stable and fast convergence across all experiments.

