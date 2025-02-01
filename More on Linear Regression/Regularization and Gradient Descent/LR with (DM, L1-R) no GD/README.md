### **Linear Regression with L1 Regularization (Lasso) Without Gradient Descent**  
---

## **1. Linear Regression Model**  

A linear regression model is defined as:  

**Y** = **X** **B** + $\epsilon$

where:  
- **X** is the *n* X *p* design matrix (with *n* observations and *p* features).  
- \(\beta\) is the \(p \times 1\) coefficient vector.  
- \(Y\) is the \(n \times 1\) response vector.  
- \(\epsilon\) is the error term (assumed to be normally distributed).  

The objective of least squares regression is to minimize the residual sum of squares (RSS):

\[
\min_{\beta} \sum_{i=1}^{n} (y_i - X_i \beta)^2
\]

where \(X_i\) is the **row vector** corresponding to the \(i\)th observation.

---

## **2. Standard Solution of OLS Regression**  

Without regularization, the **closed-form solution** of linear regression is given by:

\[
\beta = (X^T X)^{-1} X^T Y
\]

provided that \(X^T X\) is invertible.

---

## **3. Lasso Regression Formulation**  

Lasso regression adds an \(L_1\)-norm penalty to the loss function:

\[
\min_{\beta} \sum_{i=1}^{n} (y_i - X_i \beta)^2 + \lambda \sum_{j=1}^{p} |\beta_j|
\]

where:  
- \(\lambda > 0\) is the **regularization parameter** controlling sparsity.  
- \(\sum_{j=1}^{p} |\beta_j|\) is the **\(L_1\)-penalty**, which encourages sparsity by forcing some \(\beta_j\) to be exactly **zero**.

---

## **4. Reformulating the Problem Using Lagrange Multipliers**  

Instead of solving directly, we convert the constrained problem:

\[
\min_{\beta} \sum_{i=1}^{n} (y_i - X_i \beta)^2 \quad \text{subject to} \quad \sum_{j=1}^{p} |\beta_j| \leq t
\]

into the **Lagrange form**:

\[
\mathcal{L}(\beta) = \sum_{i=1}^{n} (y_i - X_i \beta)^2 + \lambda \sum_{j=1}^{p} |\beta_j|
\]

where \(\lambda\) is the **Lagrange multiplier**.

---

## **5. Differentiation of the Objective Function**  

To find the optimal \(\beta\), we take the derivative of \(\mathcal{L}(\beta)\) **w.r.t.** each coefficient \(\beta_j\).  

The squared error term expands as:

\[
\sum_{i=1}^{n} (y_i - X_i \beta)^2 = (Y - X\beta)^T (Y - X\beta)
\]

Differentiating w.r.t. \(\beta_j\):

\[
\frac{\partial}{\partial \beta_j} \sum_{i=1}^{n} (y_i - X_i \beta)^2 = -2 \sum_{i=1}^{n} x_{ij} (y_i - X_i \beta)
\]

where \(x_{ij}\) is the \(j\)th feature of the \(i\)th observation.

The derivative of the regularization term is:

\[
\frac{\partial}{\partial \beta_j} \lambda \sum_{j=1}^{p} |\beta_j| = \lambda \cdot \text{sign}(\beta_j)
\]

Setting the gradient to zero:

\[
-2 \sum_{i=1}^{n} x_{ij} (y_i - X_i \beta) + \lambda \cdot \text{sign}(\beta_j) = 0
\]

Rearranging:

\[
\sum_{i=1}^{n} x_{ij} (X_i \beta - y_i) = -\frac{\lambda}{2} \text{sign}(\beta_j)
\]

---

## **6. Soft-Thresholding Solution**  

Rearrange for \(\beta_j\):

\[
\beta_j = \frac{\sum_{i=1}^{n} x_{ij} y_i}{\sum_{i=1}^{n} x_{ij}^2} - \frac{\lambda}{2} \text{sign}(\beta_j)
\]

This is the **soft-thresholding** function:

\[
\beta_j =
\begin{cases}
\frac{\sum_{i=1}^{n} x_{ij} y_i}{\sum_{i=1}^{n} x_{ij}^2} - \frac{\lambda}{2}, & \frac{\sum_{i=1}^{n} x_{ij} y_i}{\sum_{i=1}^{n} x_{ij}^2} > \frac{\lambda}{2} \\
0, & \left| \frac{\sum_{i=1}^{n} x_{ij} y_i}{\sum_{i=1}^{n} x_{ij}^2} \right| \leq \frac{\lambda}{2} \\
\frac{\sum_{i=1}^{n} x_{ij} y_i}{\sum_{i=1}^{n} x_{ij}^2} + \frac{\lambda}{2}, & \frac{\sum_{i=1}^{n} x_{ij} y_i}{\sum_{i=1}^{n} x_{ij}^2} < -\frac{\lambda}{2}
\end{cases}
\]

Thus, **if** \(\frac{\sum_{i=1}^{n} x_{ij} y_i}{\sum_{i=1}^{n} x_{ij}^2}\) is small, \(\beta_j\) is **set to zero**, which enforces sparsity.

---

## **7. Final Direct Solution for Lasso Regression**  

The direct computation for **Lasso regression without gradient descent** follows:

1. Compute the **OLS estimate**:

   \[
   \beta_j^{OLS} = \frac{\sum_{i=1}^{n} x_{ij} y_i}{\sum_{i=1}^{n} x_{ij}^2}
   \]

2. Apply **soft-thresholding**:

   \[
   \beta_j^{Lasso} =
   \begin{cases}
   \beta_j^{OLS} - \frac{\lambda}{2}, & \beta_j^{OLS} > \frac{\lambda}{2} \\
   0, & |\beta_j^{OLS}| \leq \frac{\lambda}{2} \\
   \beta_j^{OLS} + \frac{\lambda}{2}, & \beta_j^{OLS} < -\frac{\lambda}{2}
   \end{cases}
   \]

This allows computing \(\beta\) **directly** using simple thresholding without **iterative optimization methods like gradient descent**.

---
