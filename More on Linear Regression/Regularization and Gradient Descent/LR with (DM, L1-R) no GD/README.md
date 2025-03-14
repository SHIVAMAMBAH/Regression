### **Linear Regression with L1 Regularization (Lasso) Without Gradient Descent**  
---

## **1. Linear Regression Model**  

A linear regression model is defined as:  

**Y** = **X** **B** + $\epsilon$

where:  
- **X** is the *n* X *p* design matrix (with *n* observations and *p* features).  
- **B** is the *p* X 1 coefficient vector.  
- *Y* is the *n* X 1 response vector.  
- $\epsilon$ is the error term (assumed to be normally distributed).  

The objective of least squares regression is to minimize the residual sum of squares (RSS):

![image](https://github.com/user-attachments/assets/6bccbfb8-1774-4da7-934c-46924aa58bef)


where X<sub>i</sub> is the **row vector** corresponding to the i<sup>th</sup> observation.

---

## **2. Standard Solution of OLS Regression**  

Without regularization, the **closed-form solution** of linear regression is given by:

![image](https://github.com/user-attachments/assets/f06bc1aa-a90c-4e2f-a979-ad4c10d576bf)

provided that X<sup>T</sup>T X is invertible.

---

## **3. Lasso Regression Formulation**  

Lasso regression adds an L1-norm penalty to the loss function:

![image](https://github.com/user-attachments/assets/ffef97c6-1fdf-4f27-866c-21c45c2bdbfd)


where:  
- $\lambda$ > 0 is the **regularization parameter** controlling sparsity.
  > Sparsity of the model refers to the situation where only a small number of features (or parameters) in the model have non-zero values,while the remainder are set to zero. This means that the model relies on a limited number of important predictors instead of utilizing all available features.  
- ![image](https://github.com/user-attachments/assets/7e4b4e0f-dbf9-4bba-b5e1-68ef2d7cf203)
 is the **L<sub>1</sub>-penalty**, which encourages sparsity by forcing some $\beta$ <sub>j</sub> to be exactly **zero**.

---

## **4. Reformulating the Problem Using Lagrange Multipliers**  

Instead of solving directly, we convert the constrained problem:

![image](https://github.com/user-attachments/assets/7bbde288-3497-4830-a858-765c6e930062)
  > The variable t represents a threshold for controlling the total absolute value of the coefficients. This constraint restricts the sum of the absolute values of the coefficients to be less or equal to t. By introducing the constraint with t, you effectively control the model's sparsity and compexity. A smaller value of t encourages the model to use fewer non-zero coefficients, potentially leading to better generalization and interpretability.


into the **Lagrange form**:

![image](https://github.com/user-attachments/assets/7d816308-1d31-4f3d-b3ae-b25aa4f21104)


where $\lambda$ is the **Lagrange multiplier**.

---

## **5. Differentiation of the Objective Function**  

To find the optimal $\beta$, we take the derivative of L($\beta$) **w.r.t.** each coefficient $\beta$ <sub>j</sub>.  

The squared error term expands as:

![image](https://github.com/user-attachments/assets/777dfd0e-e338-4312-a4bd-794102aae87a)


Differentiating w.r.t. $\beta$ <sub>j</sub>:

![image](https://github.com/user-attachments/assets/f97fa9d0-9d37-4beb-ba25-631148059f51)

where x<sub>ij</sub> is the j<sub>th</sub> feature of the i<sup>th</sup> observation.

The derivative of the regularization term is:

![image](https://github.com/user-attachments/assets/66168493-410b-4eb4-b7d7-9ff831b6c6fa)
  > The term sign($\beta$<sub>j</sub>) returns:  
     1 if ($\beta$<sub>j</sub>) > 0  
     -1 if ($\beta$<sub>j</sub>) < 0  
     0 if ($\beta$<sub>j</sub>) = 0  
     This indicates the direction of the gradient for each coefficient.


Setting the gradient to zero:

![image](https://github.com/user-attachments/assets/6d3c7be7-b057-44db-95f2-8b07093e2591)


Rearranging:

![image](https://github.com/user-attachments/assets/06ab15be-e120-451d-9044-307cf0d70023)


---

## **6. Soft-Thresholding Solution**  

Rearrange for $\beta$ <sub>j</sub>:

![image](https://github.com/user-attachments/assets/3639cb64-682e-465f-80b4-d41a86128a40)


This is the **soft-thresholding** function:

![image](https://github.com/user-attachments/assets/b8b3056d-7563-4886-ae5a-007585be4c5d)


Thus, **if** 
![image](https://github.com/user-attachments/assets/262cb0ac-cd40-4cf0-91fb-f6a2042aeb1d)
is small, $\beta$ <sub>j</sub> is **set to zero**, which enforces sparsity.

---

## **7. Final Direct Solution for Lasso Regression**  

The direct computation for **Lasso regression without gradient descent** follows:

1. Compute the **OLS estimate**:

   ![image](https://github.com/user-attachments/assets/58591c04-a060-4c7e-a3c3-28d69d488826)


2. Apply **soft-thresholding**:

  ![image](https://github.com/user-attachments/assets/a3cdb383-8aa4-4cdc-a0cd-444267ae6ace)


This allows computing $\beta$ **directly** using simple thresholding without **iterative optimization methods like gradient descent**.

---
