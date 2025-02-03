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

The objective is to find $\beta$ that minimizes the loss function.

---

## **2. Objective Function with L2 Regularization**
In Ridge Regression, we modify the standard **Mean Squared Error (MSE)** loss function by adding an **L2 regularization** term:

![image](https://github.com/user-attachments/assets/14d438fb-9d4a-4aa5-8f9f-8f2ea2bc1a47)


Where:
- The first term ![image](https://github.com/user-attachments/assets/a5e70381-694c-455f-ba3c-f892710719b4)
 is the **MSE loss**.
- The second term ![image](https://github.com/user-attachments/assets/69c577e0-b150-498d-8dae-3b2f67a4bb21)
 is the **L2 penalty**, which prevents large coefficients and helps reduce overfitting.
- $\lambda$ is the **regularization parameter** that controls the strength of regularization.

---

## **3. Compute the Gradient**

To apply **Gradient Descent**, we need to compute the gradient of the loss function with respect to $\beta$.

### **3.1. Gradient of the MSE Term**
The gradient of the MSE term:

![image](https://github.com/user-attachments/assets/bc6a998b-c1f3-4a15-9407-913290823497)


Expanding the squared term:

![image](https://github.com/user-attachments/assets/90dfe2f9-7ed8-4255-ba06-356941ef0986)


Differentiating with respect to \(\beta\):

![image](https://github.com/user-attachments/assets/4a0b4bad-b01e-4a28-a085-75bf0d1eadd9)


---

### **3.2. Gradient of the L2 Regularization Term**
The L2 regularization term is:

![image](https://github.com/user-attachments/assets/943d2b93-44ea-495e-811b-88a3ab3e8ea3)


Taking the derivative with respect to \(\beta\):

![image](https://github.com/user-attachments/assets/29bc5142-ae08-4a71-8c5d-ec92cc5d0140)


---

## **4. Combined Gradient**
The total gradient of the loss function:

![image](https://github.com/user-attachments/assets/6a59b09b-d024-4c18-b2af-4d42898007fe)


---

## **5. Gradient Descent Update Rule**
To minimize the loss function using **Gradient Descent**, we update $\beta$ iteratively:

![image](https://github.com/user-attachments/assets/eb756789-a177-417a-879a-ce61e08cfcc4)


Substituting the computed gradient:

![image](https://github.com/user-attachments/assets/a6b5bc36-0394-4667-a7de-e6a0694d95ad)


Simplifying:

\[
![image](https://github.com/user-attachments/assets/b92565d2-d774-4745-bdfe-46a119b1f78b)


---

## **6. Role of L2 Regularization**
- The term **- 2 $\eta$ $\lambda$ $\beta$<sup>(t)</sup>** prevents coefficients from growing too large.
- Unlike L1 regularization (Lasso), which forces some coefficients to become exactly **zero**, L2 regularization **shrinks** the coefficients but does not make them zero.
- This helps reduce overfitting while retaining all features in the model.

---

## **7. Steps for Applying Gradient Descent**
To apply gradient descent for Ridge Regression:

1. **Initialize** $\beta$<sup>(0)</sup> (random values or zeros).
2. **Set** the learning rate $\eta$.
3. **Set** the regularization parameter $\lambda$.
4. **Repeat** the following steps until convergence:
   - Compute the gradient: ![image](https://github.com/user-attachments/assets/c71c0634-db43-445c-9152-d5678d7075d9)
.
   - Update $\beta$:  
     ![image](https://github.com/user-attachments/assets/82eb0a96-fe99-494c-a88d-805a9c71c85d)

5. **Stop** when $\beta$<sup>(t)</sup> converges or a maximum number of iterations is reached.

---
