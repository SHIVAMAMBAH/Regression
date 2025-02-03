### **Linear Regression with Gradient Descent and L1 Regularization (Lasso)**
---

### **1. Linear Regression Model**

The model is the same as in regular linear regression:


**Y** = **X** $\beta$ + $\epsilon$


Where:  
- **Y** in R<sup>n+1</sup> is the response vector (dependent variable).  
- **X** in R<sup>nxp</sup> is the design matrix (features or independent variables).  
- $\beta$ in R<sup>px1</sup> is the coefficient vector (parameters to be learned).  
- $\epsilon$ is the error term (assumed to be normally distributed).

We aim to find the values of $\beta$ that minimize the loss function.

---

### **2. Objective Function with L1 Regularization**

The objective function in **Linear Regression with L1 Regularization** is:

![image](https://github.com/user-attachments/assets/1906e893-067e-402b-aa09-199a3feb1ab9)


Where:
- The first term ![image](https://github.com/user-attachments/assets/9856a74a-2597-4ac9-9d5e-9a0679523f93)
 is the **Mean Squared Error (MSE)**.
- The second term ![image](https://github.com/user-attachments/assets/344e20e3-6e16-4507-8fef-7f92d674508a)
 is the **L1 regularization** (Lasso), which encourages sparsity in the coefficients (i.e., forcing some coefficients to become zero).
- $\lambda$ is the regularization parameter that controls the strength of the regularization.

The goal is to minimize this objective function with respect to $\beta$.

---

### **3. Gradient of the Loss Function**

We need to compute the gradient of the objective function with respect to $\beta$ in order to apply gradient descent.

#### **3.1. Gradient of the MSE Term**

The gradient of the Mean Squared Error (MSE) term is:

![image](https://github.com/user-attachments/assets/33fe437a-b4ac-4fba-90f5-33993a610377)


Where:
- X<sup>T</sup>is the transpose of the design matrix.
- (Y- X $\beta$) is the residual vector (difference between actual and predicted values).

#### **3.2. Gradient of the L1 Regularization Term**

The gradient of the L1 regularization term is not straightforward, as the absolute value function | $\beta$ <sub>j</sub> | is non-differentiable at zero. However, the **subdifferential** of | $\beta$ <sub>j</sub> | is the **sign function**:

![image](https://github.com/user-attachments/assets/27ce15d3-a214-4617-abb1-97e3314e82f9)


Where:
- sign($\beta$ <sub>j</sub>) is the **sign function**, which returns 1 for positive $\beta$<sub>j</sub>, -1 for negative $\beta$<sub>j</sub>, and 0 for $\beta$<sub>j</sub> = 0.

Thus, the gradient of the L1 penalty term with respect to $\beta$ is:

![image](https://github.com/user-attachments/assets/5b65be40-6bce-4877-8e34-b1820ce53e0f)


Where:
- sign($\beta$) is applied element-wise to the vector $\beta$.

---

### **4. Combined Gradient**

The combined gradient of the full objective function is the sum of the gradients of the MSE term and the L1 regularization term:

![image](https://github.com/user-attachments/assets/cddfb4ae-4887-4273-af1f-df37dfdedad5)

---

### **5. Gradient Descent Update Rule**

To minimize the objective function using **gradient descent**, we update $\beta$ iteratively:

![image](https://github.com/user-attachments/assets/a76954e8-2cf5-4db4-b266-5f2aaa36837c)


Where:
- $\eta$ is the learning rate.
- $\beta$ <sup>(t)</sup> is the value of $\beta$ at iteration t.

Substituting the gradient into this update rule:

![image](https://github.com/user-attachments/assets/9cb7eac1-6f22-4dae-ad27-81d9959fa260)


Simplifying:

![image](https://github.com/user-attachments/assets/b35b1b0a-4b8d-4349-9dc1-8f8f743687a0)


---

### **6. The Role of the Learning Rate $\eta$**

The learning rate $\eta$ determines the size of the steps we take during the optimization process. If $\eta$ is too large, the updates may overshoot the optimal solution, while if $\eta$ is too small, the convergence may be slow.

---

### **7. Steps for Applying Gradient Descent**

To apply gradient descent for Lasso regression, the steps are as follows:

1. **Initialize** $\beta$<sup>(0)</sup> (can be zeros or random values).
2. **Set** the learning rate $\eta$.
3. **Set** the regularization parameter $\lambda$.
4. **Repeat** the following steps until convergence:
   - Compute the gradient of the objective function: ![image](https://github.com/user-attachments/assets/32b512ec-df59-47c4-872b-83eeef244eb6)
 = ![image](https://github.com/user-attachments/assets/cad449e2-3b00-4033-b176-e817f0576be6)
).
   - Update the coefficient vector: ![image](https://github.com/user-attachments/assets/fbc92362-5afc-4643-a23b-20d9303d3dd2)

5. **Stop** when the coefficients $\beta$<sup>(t)</sup> converge or the maximum number of iterations is reached.

---
