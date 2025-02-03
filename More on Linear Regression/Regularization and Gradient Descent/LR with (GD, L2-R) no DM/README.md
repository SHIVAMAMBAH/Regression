### **Linear Regression with Gradient Descent and L2 Regularization (Ridge Regression)**

---

## **1. Linear Regression Model**
The standard linear regression model is:

Y = X $\beta$ + $\epsilon$


Where:  
- Y in R<sup>n+1</sup> is the target variable (dependent variable).  
- X in R<sup>nxp</sup> is the feature matrix (independent variables).  
- $\beta$ in R<sup>px1</sup> is the coefficient vector (parameters to be learned).  
- $\epsilon$ is the error term.

The objective is to find \(\beta\) that minimizes the loss function.

---

## **2. Objective Function with L2 Regularization**
In Ridge Regression, we modify the standard **Mean Squared Error (MSE)** loss function by adding an **L2 regularization** term:

\[
\mathcal{L}(\beta) = \sum_{i=1}^{n} (y_i - x_i^T \beta)^2 + \lambda \sum_{j=1}^{p} \beta_j^2
\]

Where:
- The first term \(\sum_{i=1}^{n} (y_i - x_i^T \beta)^2\) is the **MSE loss**.
- The second term \(\lambda \sum_{j=1}^{p} \beta_j^2\) is the **L2 penalty**, which prevents large coefficients and helps reduce overfitting.
- \(\lambda\) is the **regularization parameter** that controls the strength of regularization.

---

## **3. Compute the Gradient**

To apply **Gradient Descent**, we need to compute the gradient of the loss function with respect to \(\beta\).

### **3.1. Gradient of the MSE Term**
The gradient of the MSE term:

\[
\nabla_{\beta} \sum_{i=1}^{n} (y_i - x_i^T \beta)^2
\]

Expanding the squared term:

\[
(y_i - x_i^T \beta)^2 = y_i^2 - 2 y_i x_i^T \beta + (x_i^T \beta)^2
\]

Differentiating with respect to \(\beta\):

\[
\nabla_{\beta} \sum_{i=1}^{n} (y_i - x_i^T \beta)^2 = -2 X^T (Y - X\beta)
\]

---

### **3.2. Gradient of the L2 Regularization Term**
The L2 regularization term is:

\[
\lambda \sum_{j=1}^{p} \beta_j^2
\]

Taking the derivative with respect to \(\beta\):

\[
\nabla_{\beta} \left( \lambda \sum_{j=1}^{p} \beta_j^2 \right) = 2 \lambda \beta
\]

---

## **4. Combined Gradient**
The total gradient of the loss function:

\[
\nabla_{\beta} \mathcal{L}(\beta) = -2 X^T (Y - X\beta) + 2 \lambda \beta
\]

---

## **5. Gradient Descent Update Rule**
To minimize the loss function using **Gradient Descent**, we update \(\beta\) iteratively:

\[
\beta^{(t+1)} = \beta^{(t)} - \eta \nabla_{\beta} \mathcal{L}(\beta^{(t)})
\]

Substituting the computed gradient:

\[
\beta^{(t+1)} = \beta^{(t)} - \eta \left( -2 X^T (Y - X\beta^{(t)}) + 2 \lambda \beta^{(t)} \right)
\]

Simplifying:

\[
\beta^{(t+1)} = \beta^{(t)} + 2 \eta X^T (Y - X\beta^{(t)}) - 2 \eta \lambda \beta^{(t)}
\]

---

## **6. Role of L2 Regularization**
- The term **\(- 2 \eta \lambda \beta^{(t)}\)** prevents coefficients from growing too large.
- Unlike L1 regularization (Lasso), which forces some coefficients to become exactly **zero**, L2 regularization **shrinks** the coefficients but does not make them zero.
- This helps reduce overfitting while retaining all features in the model.

---

## **7. Steps for Applying Gradient Descent**
To apply gradient descent for Ridge Regression:

1. **Initialize** \(\beta^{(0)}\) (random values or zeros).
2. **Set** the learning rate \(\eta\).
3. **Set** the regularization parameter \(\lambda\).
4. **Repeat** the following steps until convergence:
   - Compute the gradient: \(\nabla_{\beta} \mathcal{L}(\beta^{(t)}) = -2 X^T (Y - X \beta^{(t)}) + 2 \lambda \beta^{(t)}\).
   - Update \(\beta\):  
     \[
     \beta^{(t+1)} = \beta^{(t)} + 2 \eta X^T (Y - X \beta^{(t)}) - 2 \eta \lambda \beta^{(t)}
     \]
5. **Stop** when \(\beta^{(t)}\) converges or a maximum number of iterations is reached.

---
