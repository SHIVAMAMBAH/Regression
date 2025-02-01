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
- ![image](https://github.com/user-attachments/assets/7e4b4e0f-dbf9-4bba-b5e1-68ef2d7cf203)
 is the **L<sub>1</sub>-penalty**, which encourages sparsity by forcing some $\beta$ <sub>j</sub> to be exactly **zero**.

---

## **4. Reformulating the Problem Using Lagrange Multipliers**  

Instead of solving directly, we convert the constrained problem:

![image](https://github.com/user-attachments/assets/7bbde288-3497-4830-a858-765c6e930062)


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

where x<sub>ij</sub is the j<sub>th</sub> feature of the i<sup>th</sup> observation.

The derivative of the regularization term is:

![image](https://github.com/user-attachments/assets/66168493-410b-4eb4-b7d7-9ff831b6c6fa)


Setting the gradient to zero:

![image](https://github.com/user-attachments/assets/6d3c7be7-b057-44db-95f2-8b07093e2591)


Rearranging:

![image](https://github.com/user-attachments/assets/06ab15be-e120-451d-9044-307cf0d70023)


---

## **6. Soft-Thresholding Solution**  

Rearrange for \(\beta_j\):

![image](https://github.com/user-attachments/assets/3639cb64-682e-465f-80b4-d41a86128a40)


This is the **soft-thresholding** function:

![image](https://github.com/user-attachments/assets/b8b3056d-7563-4886-ae5a-007585be4c5d)


Thus, **if** 
![image](https://github.com/user-attachments/assets/262cb0ac-cd40-4cf0-91fb-f6a2042aeb1d)
is small, \(\beta_j\) is **set to zero**, which enforces sparsity.

---

## **7. Final Direct Solution for Lasso Regression**  

The direct computation for **Lasso regression without gradient descent** follows:

1. Compute the **OLS estimate**:

   ![image](https://github.com/user-attachments/assets/58591c04-a060-4c7e-a3c3-28d69d488826)


2. Apply **soft-thresholding**:

  ![image](https://github.com/user-attachments/assets/a3cdb383-8aa4-4cdc-a0cd-444267ae6ace)


This allows computing \(\beta\) **directly** using simple thresholding without **iterative optimization methods like gradient descent**.

---
