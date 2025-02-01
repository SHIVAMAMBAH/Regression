### **Linear Regression with \(L_2\) Regularization (Ridge Regression) Without Gradient Descent**

---

## **1. Linear Regression Model**  

The linear regression model is the same as in the previous case:

**Y**  = **X** **$\beta$** + $\epsilon$

where:  
- **X** is the n X p design matrix (with \(n\) observations and \(p\) features).  
- **$\beta$** is the p X 1 coefficient vector.  
- **Y** is the n X 1 response vector.  
- $\epsilon$ is the error term.

The objective of least squares regression is to minimize the residual sum of squares (RSS):

\[
\min_{\beta} \sum_{i=1}^{n} (y_i - X_i \beta)^2
\]

where \(X_i\) is the **row vector** corresponding to the \(i\)-th observation.

---

## **2. Ridge Regression Formulation**

Ridge regression adds an \(L_2\)-norm penalty (also known as **Tikhonov regularization**) to the least squares objective:

\[
\min_{\beta} \sum_{i=1}^{n} (y_i - X_i \beta)^2 + \lambda \sum_{j=1}^{p} \beta_j^2
\]

where:  
- \(\lambda > 0\) is the **regularization parameter** controlling the magnitude of \(\beta\).  
- \(\sum_{j=1}^{p} \beta_j^2\) is the **\(L_2\)-penalty** that shrinks the coefficients \(\beta_j\), but does not set them to zero.

---

## **3. Reformulating the Problem Using Lagrange Multipliers**

We can convert this **constrained optimization** problem into an unconstrained form using **Lagrange multipliers**. Instead of minimizing:

\[
\min_{\beta} \sum_{i=1}^{n} (y_i - X_i \beta)^2 \quad \text{subject to} \quad \sum_{j=1}^{p} \beta_j^2 \leq t
\]

we write the **Lagrange function**:

\[
\mathcal{L}(\beta) = \sum_{i=1}^{n} (y_i - X_i \beta)^2 + \lambda \sum_{j=1}^{p} \beta_j^2
\]

where \(\lambda\) is the **Lagrange multiplier**.

---

## **4. Differentiation of the Objective Function**

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
\frac{\partial}{\partial \beta_j} \lambda \sum_{j=1}^{p} \beta_j^2 = 2\lambda \beta_j
\]

Setting the gradient to zero:

\[
-2 \sum_{i=1}^{n} x_{ij} (y_i - X_i \beta) + 2\lambda \beta_j = 0
\]

Rearranging:

\[
\sum_{i=1}^{n} x_{ij} (X_i \beta - y_i) = \lambda \beta_j
\]

---

## **5. Solving for \(\beta\)**  

Rearrange for \(\beta_j\):

\[
\beta_j = \frac{\sum_{i=1}^{n} x_{ij} (y_i - X_i \beta)}{\lambda + \sum_{i=1}^{n} x_{ij}^2}
\]

We have a system of equations for all \(\beta_j\). However, this system can be solved **directly** by using matrix algebra for all coefficients at once.

---

## **6. Matrix Formulation**

We rewrite the objective function in matrix form:

\[
\min_{\beta} (Y - X \beta)^T (Y - X \beta) + \lambda \beta^T \beta
\]

The normal equation for this problem is derived by differentiating the objective function with respect to \(\beta\) and setting it equal to zero:

\[
-2 X^T (Y - X \beta) + 2 \lambda \beta = 0
\]

Rearranging:

\[
X^T X \beta + \lambda \beta = X^T Y
\]

Now, factoring out \(\beta\) from the left side:

\[
(X^T X + \lambda I) \beta = X^T Y
\]

where \(I\) is the \(p \times p\) identity matrix. This is the **Ridge regression normal equation**.

---

## **7. Final Direct Solution for Ridge Regression**

To solve for \(\beta\), multiply both sides by \((X^T X + \lambda I)^{-1}\):

\[
\beta = (X^T X + \lambda I)^{-1} X^T Y
\]

Thus, the **direct solution for Ridge regression** is:

\[
\beta = (X^T X + \lambda I)^{-1} X^T Y
\]

This solution requires the matrix \(X^T X + \lambda I\) to be invertible, which is guaranteed when \(\lambda > 0\).

---
