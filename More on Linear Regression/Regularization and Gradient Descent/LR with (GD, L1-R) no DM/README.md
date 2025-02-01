### **Linear Regression with Gradient Descent and L1 Regularization (Lasso)**
---

### **1. Linear Regression Model**

The model is the same as in regular linear regression:


**Y** = **X** $\beta$ + $\epsilon$


Where:  
- **Y** in \mathbb{R}^{n \times 1} \) is the response vector (dependent variable).  
- **X** in \mathbb{R}^{n \times p} \) is the design matrix (features or independent variables).  
- $\beta$ in \mathbb{R}^{p \times 1} \) is the coefficient vector (parameters to be learned).  
- $\epsilon$ is the error term (assumed to be normally distributed).

We aim to find the values of $\beta$ that minimize the loss function.

---

### **2. Objective Function with L1 Regularization**

The objective function in **Linear Regression with L1 Regularization** is:

\[
\mathcal{L}(\beta) = \sum_{i=1}^{n} (y_i - x_i^T \beta)^2 + \lambda \sum_{j=1}^{p} |\beta_j|
\]

Where:
- The first term \(\sum_{i=1}^{n} (y_i - x_i^T \beta)^2\) is the **Mean Squared Error (MSE)**.
- The second term \(\lambda \sum_{j=1}^{p} |\beta_j|\) is the **L1 regularization** (Lasso), which encourages sparsity in the coefficients (i.e., forcing some coefficients to become zero).
- \(\lambda\) is the regularization parameter that controls the strength of the regularization.

The goal is to minimize this objective function with respect to $\beta$.

---

### **3. Gradient of the Loss Function**

We need to compute the gradient of the objective function with respect to \(\beta\) in order to apply gradient descent.

#### **3.1. Gradient of the MSE Term**

The gradient of the Mean Squared Error (MSE) term is:

\[
\nabla_{\beta} \left( \sum_{i=1}^{n} (y_i - x_i^T \beta)^2 \right) = -2X^T (Y - X\beta)
\]

Where:
- \( X^T \) is the transpose of the design matrix.
- \( (Y - X\beta) \) is the residual vector (difference between actual and predicted values).

#### **3.2. Gradient of the L1 Regularization Term**

The gradient of the L1 regularization term is not straightforward, as the absolute value function \(|\beta_j|\) is non-differentiable at zero. However, the **subdifferential** of \(|\beta_j|\) is the **sign function**:

\[
\nabla_{\beta_j} \lambda |\beta_j| = \lambda \, \text{sign}(\beta_j)
\]

Where:
- \(\text{sign}(\beta_j)\) is the **sign function**, which returns \(1\) for positive \(\beta_j\), \(-1\) for negative \(\beta_j\), and \(0\) for \(\beta_j = 0\).

Thus, the gradient of the L1 penalty term with respect to \(\beta\) is:

\[
\nabla_{\beta} \left( \lambda \sum_{j=1}^{p} |\beta_j| \right) = \lambda \, \text{sign}(\beta)
\]

Where:
- \(\text{sign}(\beta)\) is applied element-wise to the vector \(\beta\).

---

### **4. Combined Gradient**

The combined gradient of the full objective function is the sum of the gradients of the MSE term and the L1 regularization term:

\[
\nabla_{\beta} \mathcal{L}(\beta) = -2 X^T (Y - X \beta) + \lambda \, \text{sign}(\beta)
\]

---

### **5. Gradient Descent Update Rule**

To minimize the objective function using **gradient descent**, we update \(\beta\) iteratively:

\[
\beta^{(t+1)} = \beta^{(t)} - \eta \nabla_{\beta} \mathcal{L}(\beta^{(t)})
\]

Where:
- \( \eta \) is the learning rate.
- \(\beta^{(t)}\) is the value of \(\beta\) at iteration \(t\).

Substituting the gradient into this update rule:

\[
\beta^{(t+1)} = \beta^{(t)} - \eta \left( -2 X^T (Y - X \beta^{(t)}) + \lambda \, \text{sign}(\beta^{(t)}) \right)
\]

Simplifying:

\[
\beta^{(t+1)} = \beta^{(t)} + 2 \eta X^T (Y - X \beta^{(t)}) - \eta \lambda \, \text{sign}(\beta^{(t)})
\]

---

### **6. The Role of the Learning Rate \(\eta\)**

The learning rate \(\eta\) determines the size of the steps we take during the optimization process. If \(\eta\) is too large, the updates may overshoot the optimal solution, while if \(\eta\) is too small, the convergence may be slow.

---

### **7. Steps for Applying Gradient Descent**

To apply gradient descent for Lasso regression, the steps are as follows:

1. **Initialize** \(\beta^{(0)}\) (can be zeros or random values).
2. **Set** the learning rate \(\eta\).
3. **Set** the regularization parameter \(\lambda\).
4. **Repeat** the following steps until convergence:
   - Compute the gradient of the objective function: \(\nabla_{\beta} \mathcal{L}(\beta^{(t)}) = -2 X^T (Y - X \beta^{(t)}) + \lambda \, \text{sign}(\beta^{(t)})\).
   - Update the coefficient vector: \(\beta^{(t+1)} = \beta^{(t)} - \eta \nabla_{\beta} \mathcal{L}(\beta^{(t)})\).
5. **Stop** when the coefficients \(\beta^{(t)}\) converge or the maximum number of iterations is reached.

---
