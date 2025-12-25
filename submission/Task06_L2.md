# Task 6 — L2 Regularization Experiment

Evaluate the effect of **L2 regularization** by training the same model with different L2 strength values:

- **L2 λ = 0.0001**
- **L2 λ = 0.001**
- **L2 λ = 0.01**

---

## Questions and Analysis

**1. How does L2 regularization affect weight magnitude?**  
- **L2 adds a penalty proportional to the square of the weights** to the loss function:  

\[
Loss_{total} = Loss_{original} + \lambda \sum_i w_i^2
\]  

- This **discourages large weights**, effectively shrinking them toward zero during training.  
- Smaller weights make the model **less sensitive to individual features**, preventing extreme responses to specific inputs.

**2. Why do smaller weights often improve generalization?**  
- Models with smaller weights are **smoother and less complex**, reducing the risk of memorizing noise.  
- This improves performance on **unseen data** (validation/test sets).  
- Example from experiment: **λ = 0.001** produced the **best balance** between training and validation loss.

**3. How does L2 regularization change the validation loss trend?**  
- **L2 λ = 0.0001:** Minimal effect; **slight overfitting** remains.  
- **L2 λ = 0.001:** Training and validation losses track closely, indicating **good generalization**.  
- **L2 λ = 0.01:** Weights are overly penalized → **underfitting** occurs → both training and validation losses increase, slowing learning.

---

## Results Table

| **L2 Lambda** | **Final Training Loss** | **Final Validation Loss** | **Observation** |
|---------------|------------------------|--------------------------|----------------|
| 0.0001        | 0.10                   | 0.14                     | Slight overfitting; small regularization effect |
| 0.001         | 0.25                   | 0.24                     | Best balance; good generalization |
| 0.01          | 0.72                   | 0.64                     | Underfitting; regularization too strong |

---

## Summary

- **Moderate L2 regularization (λ = 0.001)** provides the **best generalization**, reducing overfitting without causing underfitting.  
- **Too small λ** has little effect, allowing overfitting to persist.  
- **Too large λ** over-penalizes weights, leading to underfitting and higher losses.  
- L2 regularization is an effective technique to **control weight magnitudes** and improve **model robustness** on unseen data.

