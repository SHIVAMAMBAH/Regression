### **Linear Regression with Both \(L_1\) and \(L_2\) Regularization (Elastic Net) Without Gradient Descent**

In this case, we combine both **L1 regularization (Lasso)** and **L2 regularization (Ridge)** to create an **Elastic Net** model. This approach is particularly useful for handling situations where there are many correlated features and for regularization when we expect both sparsity and smoothness in the model.

---

## **1. Linear Regression Model**  

The linear regression model is the same as before:

**Y** = **X** $\beta$ + $\epsilon$

where:  
- **Y** is the n X 1 response vector.  
- **X** is the n X p design matrix.  
- $\beta$ is the p X 1 coefficient vector.  
- $\epsilon$ is the error term.

---

## **2. Elastic Net Regularization Formulation**

In **Elastic Net**, the objective function combines both \(L_1\) and \(L_2\) regularization terms:

![image](https://github.com/user-attachments/assets/3e1f8c56-9356-4eb9-95fd-26578ac5c897)


where:  
- \(\lambda_1 > 0\) is the regularization parameter for **L1 regularization** (Lasso).  
- \(\lambda_2 > 0\) is the regularization parameter for **L2 regularization** (Ridge).  
- \(\sum_{j=1}^{p} |\beta_j|\) is the **\(L_1\)-norm penalty** that encourages sparsity in the coefficients.  
- \(\sum_{j=1}^{p} \beta_j^2\) is the **\(L_2\)-norm penalty** that encourages small coefficients but does not promote sparsity.

---

## **3. Differentiation of the Objective Function**

We need to minimize the following:

![image](https://github.com/user-attachments/assets/86e06f11-616c-4d3e-acc3-bd12047aa872)


We first take the derivative of the first part, the residual sum of squares (RSS):

![image](https://github.com/user-attachments/assets/18dcc4bb-ebe5-4658-8ab9-3b9950dacdfb)


Next, we take the derivatives of the regularization terms.

- The derivative of the **\(L_1\)-norm** is not as straightforward because of the absolute value. The derivative of \(\sum_{j=1}^{p} |\beta_j|\) is a **subdifferential** (the derivative does not exist at \(\beta_j = 0\) but can be represented as a set of values). It is given by:

  ![image](https://github.com/user-attachments/assets/69748a02-b28b-491d-abdc-442e9041233a)


- The derivative of the **\(L_2\)-norm** is straightforward:

  ![image](https://github.com/user-attachments/assets/e7e1dc74-27c4-45d7-9f22-91e91d20843f)


Thus, the total derivative is:

![image](https://github.com/user-attachments/assets/dc5de3e4-60f9-4bcc-8731-a791d450e05e)


Rearranging:

![image](https://github.com/user-attachments/assets/c4c590d0-9c49-4cf4-9201-7f105de0bc61)


---

## **4. Matrix Formulation**

Rewriting the above equation in matrix form:

![image](https://github.com/user-attachments/assets/86e47af9-3a5c-48de-99e1-6bb4756479d1)


The normal equation for this problem becomes:

![image](https://github.com/user-attachments/assets/2e6cd649-3589-4492-b9e8-79c3989b0c25)


Simplifying:

![image](https://github.com/user-attachments/assets/9386d351-0308-475c-9c90-4d77757f75fb)


Now, the challenge here is that the \(L_1\) term (\(\text{sign}(\beta)\)) is **non-differentiable at zero**, so a direct closed-form solution doesn't exist like it does in Ridge or Lasso regression.

---

## **5. Coordinate Descent or Iterative Methods**

Since the solution to the equation involves non-differentiable terms, **coordinate descent** or other iterative methods are typically used for solving the **Elastic Net** optimization problem. The idea behind coordinate descent is to update one coefficient at a time while keeping the others fixed.

The update rule for each \(\beta_j\) in coordinate descent is:

![image](https://github.com/user-attachments/assets/a3e2d8cb-0754-4b9b-bdd3-e05832a42b87)


where \(S(a) = \text{sign}(a) \max(0, |a| - \lambda_1)\) is the **soft-thresholding** operator that implements the **L1 regularization** (Lasso).

---
