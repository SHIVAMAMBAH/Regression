### **Linear Regression with L2 Regularization (Ridge Regression) Without Gradient Descent**

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

![image](https://github.com/user-attachments/assets/cf9098c1-ef3d-4053-86d3-328671a4014f)


where **X** <sub>i</sub> is the **row vector** corresponding to the i-th observation.

---

## **2. Ridge Regression Formulation**

Ridge regression adds an \(L_2\)-norm penalty (also known as **Tikhonov regularization**) to the least squares objective:

![image](https://github.com/user-attachments/assets/d807c0d0-7355-47b3-b704-4dfe162c4d59)


where:  
- $\lambda$ > 0 is the **regularization parameter** controlling the magnitude of \(\beta\).  
- ![image](https://github.com/user-attachments/assets/140b1802-6d26-481d-83fb-101c301e2a19)
 is the **\(L_2\)-penalty** that shrinks the coefficients $\beta$<sub>j</sub>, but does not set them to zero.

---

## **3. Reformulating the Problem Using Lagrange Multipliers**

We can convert this **constrained optimization** problem into an unconstrained form using **Lagrange multipliers**. Instead of minimizing:

![image](https://github.com/user-attachments/assets/33783dc3-8556-4c89-b2d2-5a63c08e821d)


we write the **Lagrange function**:

![image](https://github.com/user-attachments/assets/b3484c32-45ed-4c12-92fa-80d24560df9d)


where $\lambda$ is the **Lagrange multiplier**.

---

## **4. Differentiation of the Objective Function**

To find the optimal $\beta$, we take the derivative of L($\beta$) **w.r.t.** each coefficient $\beta$<sub>j</sub>.  

The squared error term expands as:

![image](https://github.com/user-attachments/assets/e6efeb1b-b03d-48d5-ae2a-a8eb936e1d54)


Differentiating w.r.t. $\beta$<sub>j</sub>:

![image](https://github.com/user-attachments/assets/bbbc3a92-075e-44b3-b81c-61a5a522fe58)


where X<sub>ij</sub> is the j-th feature of the i-th observation.

The derivative of the regularization term is:

![image](https://github.com/user-attachments/assets/6100d19f-6855-492d-96a6-d06bd8eb35bd)


Setting the gradient to zero:

![image](https://github.com/user-attachments/assets/f7a83507-b328-42d6-aae3-c81090b234d3)


Rearranging:

![image](https://github.com/user-attachments/assets/6cf6f458-4429-4035-9566-5622fcb8987d)

---

## **5. Solving for $\beta$<sub>j</sub>**  

Rearrange for $\beta$<sub>j</sub>:

![image](https://github.com/user-attachments/assets/304666b5-cfa0-4a47-a55f-08551c226649)


We have a system of equations for all $\beta$<sub>j</sub>. However, this system can be solved **directly** by using matrix algebra for all coefficients at once.

---

## **6. Matrix Formulation**

We rewrite the objective function in matrix form:

![image](https://github.com/user-attachments/assets/4628fde4-5365-4569-a4ff-42cdda81ba4f)


The normal equation for this problem is derived by differentiating the objective function with respect to $\beta$<sub>j</sub> and setting it equal to zero:

![image](https://github.com/user-attachments/assets/5421bf03-80e1-4b6f-aa99-3a69546bb9ce)


Rearranging:

![image](https://github.com/user-attachments/assets/d6935023-9a56-40ad-8ec3-91058cd2eb8b)


Now, factoring out $\beta$<sub>j</sub> from the left side:

![image](https://github.com/user-attachments/assets/4cfb6b79-7a74-4a65-ae49-7dc3a9d5759d)


where I is the p X p identity matrix. This is the **Ridge regression normal equation**.

---

## **7. Final Direct Solution for Ridge Regression**

To solve for $\beta$<sub>j</sub>, multiply both sides by (X<sup>T</sup> X + $\lambda$ I)<sup>-1</sup>:

![image](https://github.com/user-attachments/assets/26183ddb-6617-4272-b90a-6582e51ff94a)


Thus, the **direct solution for Ridge regression** is:

![image](https://github.com/user-attachments/assets/fe7f7619-d41f-4f20-bdfc-a3fc8c1e8547)


This solution requires the matrix X<sup>T</sup> X + $\lambda$ I to be invertible, which is guaranteed when $\lambda$ > 0.

---
