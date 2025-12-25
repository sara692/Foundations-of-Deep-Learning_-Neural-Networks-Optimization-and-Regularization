# Task 5 — Dropout Ablation Study

Evaluate the effect of **Dropout regularization** by training the same model with different dropout rates:

- **No Dropout**
- **Dropout = 0.1**
- **Dropout = 0.3**

---

## Questions and Analysis

**1. How does overfitting differ between the three configurations?**  
- **No Dropout:** Training loss decreased rapidly while validation loss stopped improving and fluctuated, creating a clear gap between the two curves. This indicates **strong overfitting**.  
- **Dropout = 0.1:** Training and validation loss curves decreased smoothly and remained close throughout training, showing **minimal overfitting** and **good generalization**.  
- **Dropout = 0.3:** Both losses decreased slowly and stayed relatively high. Although the gap was small, the higher loss values indicate **underfitting** caused by **excessive regularization**.  

**2. Which Dropout value provides the best generalization performance?**  
- **Dropout = 0.1** provided the **best generalization performance**. It reduced overfitting effectively while preserving sufficient model capacity to learn meaningful features from the data.

**3. Why does training without Dropout lead to overfitting?**  
- Without Dropout, **all neurons remain active** during training, allowing them to **co-adapt** and rely on specific feature combinations.  
- This encourages **memorization of training data** rather than learning generalized representations, resulting in poor validation performance.

**4. Explain how Dropout prevents neuron co-adaptation and improves robustness.**  
- **Dropout** randomly deactivates a subset of neurons during each training iteration. This forces the remaining neurons to **learn features independently**, rather than depending on specific other neurons.  

As a result:  
- Feature representations become **more distributed and redundant**  
- The network behaves like an **ensemble of multiple sub-networks**  
- Learned features are **more robust to noise and unseen data**  

- During inference, **all neurons are active**, allowing the model to benefit from full capacity while retaining the **robustness learned during training**.

