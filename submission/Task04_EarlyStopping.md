# Task 4 — EarlyStopping Behavior Analysis

Enable EarlyStopping with:

keras.callbacks.EarlyStopping(patience=3, restore_best_weights=True)
---

### Questions and Analysis

**1. At which epoch did training stop?**  
With Adam and `patience=3`, training stopped at **epoch 9**. This happened because the **validation loss (`val_loss`)** did not improve for 3 consecutive epochs after reaching its minimum around epoch 6 (0.0667).

**2. Why does the validation loss control this decision?**  
EarlyStopping monitors `val_loss` by default to prevent **overfitting**. Once `val_loss` stops decreasing, continuing training risks fitting the training data too closely, which may **degrade generalization performance**.

**3. What happens if you increase patience (e.g., to 5)?**  
Increasing patience allows the model to **wait longer before stopping**, giving additional epochs for potential improvements.  

- With `patience=5`, training continued up to **epoch 14**, allowing more chance to improve `val_loss` and validation accuracy.  
- However, it slightly increases the risk of **overfitting**, since the model may train beyond the optimal point.

**4. Would a different optimizer (e.g., SGD) change the EarlyStopping pattern?**  
Yes. SGD converges **slower** than Adam, so `val_loss` decreases more gradually. With the same patience, EarlyStopping would likely **trigger later** for SGD, requiring more epochs to reach a comparable minimum `val_loss`.

**5. Explain how EarlyStopping acts as an indirect form of regularization ** 
EarlyStopping prevents overfitting by **halting training once the validation metric stops improving**. It effectively **limits the number of epochs** the model trains on the data, which indirectly controls model complexity without adding explicit penalties like L1/L2 regularization. This ensures better generalization to unseen data.

---

**Conclusion**  
EarlyStopping balances **underfitting and overfitting**, allowing sufficient training while avoiding unnecessary epochs. Both **patience** and **optimizer choice** directly influence when training stops and the final validation performance.

