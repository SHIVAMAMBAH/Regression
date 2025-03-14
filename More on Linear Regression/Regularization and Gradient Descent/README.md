**Linear Regression** can be solved with or without **Regularizarion** and with or without **Gradient Descent**. We will see When to use them or when not. Whether you use it depends on factors like *dataset size*, *feature count*, and *computational efficiency*.

---
### Effect of Data Type on Choice (Direct Method or Gradient Descent)
- **Small datasets (e.g., 1000 samples, 10 features)** → Normal Equation is better.
- **Large datasets (e.g., millions of samples, 1000+ features)** → Gradient Descent is better.
---

### While Regularization is used in *Overfitting* and *Underfitting* Cases

---

## **Table: Linear Regression Methods with Direct Method, Regularization, and Gradient Descent**

| **Method**            | **Direct Method** | **Regularization** | **Gradient Descent** | **Combination Name**                          | **When to Use?**                      | **Pros**                              | **Cons**                                       |
|-----------------------|-------------------|--------------------|----------------------|----------------------------------------------|--------------------------------------|---------------------------------------|------------------------------------------------|
| **Linear Regression**  | ✅ Yes            | ❌ No               | ❌ No                 | Simple Linear Regression (Normal Equation)   | Small dataset, low-dimensional data | Exact solution, fast for small data   | Slow for large datasets (O(m<sup>3</sup>))      |
| **Linear Regression**  | ❌ No             | ❌ No               | ✅ Yes                | Simple Linear Regression (Gradient Descent)  | Large datasets, high-dimensional data | Works with large datasets, avoids matrix inversion | Needs tuning (learning rate, convergence criteria) |
| **Linear Regression**  | ✅ Yes            | ✅ L2               | ❌ No                 | Ridge Regression (L2) - Normal Equation      | Small to medium dataset, avoids overfitting | Stabilizes weights, reduces multicollinearity | Computationally expensive for very large datasets |
| **Linear Regression**  | ❌ No             | ✅ L2               | ✅ Yes                | Ridge Regression (L2) - Gradient Descent     | Large dataset, avoids overfitting, too large for normal equation | Works with large datasets | Slower convergence than normal equation |
| **Linear Regression**  | ❌ No             | ✅ L1               | ✅ Yes                | Lasso Regression (L1) - Gradient Descent     | Feature selection, high-dimensional sparse data | Sets some weights to exactly zero (sparse model) | No closed-form solution, requires iterative methods |
| **Linear Regression**  | ✅ Yes            | ✅ L1               | ❌ No                 | Lasso Regression (L1) - Normal Equation      | Small to medium dataset, feature selection | Exact solution, sparsity in coefficients | Computationally expensive for very large datasets |
| **Linear Regression**  | ✅ Yes            | ✅ L1 & L2          | ❌ No                 | Elastic Net (L1 + L2) - Normal Equation      | Small to medium dataset, both feature selection & stability | Exact solution, balances L1 & L2 regularization | Computationally expensive for large datasets |
| **Linear Regression**  | ❌ No             | ✅ L1 & L2          | ✅ Yes                | Elastic Net (L1 + L2) - Gradient Descent     | Both feature selection and stability, large dataset | Balances L1 & L2 benefits | Requires hyperparameter tuning ($\alpha$, $\lambda$) |

