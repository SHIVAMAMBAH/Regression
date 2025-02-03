# **Linear Regression with Gradient Descent and Both L1 & L2 Regularization (Elastic Net Regression)**  
 

---

## **1. Objective Function (Loss Function)**  
In **Elastic Net Regression**, the loss function is a combination of **Mean Squared Error (MSE)** with both **L1 (Lasso) and L2 (Ridge) regularization**:

![image](https://github.com/user-attachments/assets/e723309d-239e-4b51-a298-5f175abb3672)


where:
- **First term**: ![image](https://github.com/user-attachments/assets/6bee08e3-759c-457d-913c-e0409ad04b3c)
 → standard **MSE loss**.
- **Second term**: ![image](https://github.com/user-attachments/assets/b4bdc3d6-1937-4c65-960a-8ae8cd96fbc4)
 → **L1 penalty** (Lasso), which encourages sparsity (i.e., forcing some coefficients to be exactly **zero**).
- **Third term**: ![image](https://github.com/user-attachments/assets/353294f8-8d12-4150-8d37-c9b853798c34)
 → **L2 penalty** (Ridge), which shrinks coefficients but does not make them exactly zero.
- $\lambda$<sub>1</sub>, $\lambda$<sub>2</sub> > 0 are **regularization hyperparameters** that control the strength of L1 and L2 regularization.

---

## **2. Compute the Gradient**  
We now compute the gradient of the loss function L($\beta$) w.r.t. $\beta$.

### **2.1. Gradient of MSE Term**
The **MSE loss** term is:

![image](https://github.com/user-attachments/assets/d59122bb-49fb-4050-8fa6-db57c67acb78)


Taking its derivative w.r.t. $\beta$:

![image](https://github.com/user-attachments/assets/2b5980eb-91f0-41a6-801b-11797e6349e3)


---

### **2.2. Gradient of L1 Regularization Term (Lasso)**
The **L1 regularization** term is:

![image](https://github.com/user-attachments/assets/e7b82d05-ff96-4feb-9e1d-d6bc1b9a66e0)


The gradient of | $\beta$<sub>j</sub> | is **not differentiable at** $\beta$ <sub>j</sub> = 0. However, we use **subgradient** methods:

![image](https://github.com/user-attachments/assets/75c05eab-feef-410e-8b60-f90af31d384f)


For vector form:

![image](https://github.com/user-attachments/assets/bd432c1f-0722-4b1a-a782-93f3a477481f)


where **sign($\beta$)** is a vector function that returns:
- +1 if $\beta$<sub>j</sub> > 0,
- -1 if $\beta$<sub>j</sub> < 0,
- 0 if $\beta$<sub>j</sub> = 0.

---

### **2.3. Gradient of L2 Regularization Term (Ridge)**
The **L2 regularization** term is:

![image](https://github.com/user-attachments/assets/6d1b919b-b816-461f-9ed8-0bae0d69ad7b)


Taking the derivative:

![image](https://github.com/user-attachments/assets/9110b7de-e815-4451-a1c7-aaad278864d4)


---

## **3. Combined Gradient**  
The total gradient of the **Elastic Net loss function** is:

![image](https://github.com/user-attachments/assets/e86ff05b-5ea6-4cf8-9c34-76596c43bf6d)


---

## **4. Gradient Descent Update Rule**  
Using **Gradient Descent**, we update $\beta$ iteratively:

![image](https://github.com/user-attachments/assets/4a6fbb78-d7ed-4344-abac-b7d0bf64c4d6)


Substituting the computed gradient:

![image](https://github.com/user-attachments/assets/fc61138f-56b4-499c-a020-3d79a60269fc)


---

## **5. Elastic Net Behavior**
- The **L1 term** $\lambda$<sub>1</sub> sign($\beta$) pushes coefficients toward **zero**, enforcing sparsity.
- The **L2 term** (2 $\lambda$<sub>2</sub> $\beta$) shrinks the coefficients **without making them exactly zero**.
- Elastic Net is **useful when features are correlated**, because Lasso alone might arbitrarily pick one feature while ignoring another correlated one.

---

## **6. Steps for Gradient Descent with Elastic Net**
1. **Initialize** $\beta$<sub>(0)</sub> (random values or zeros).
2. **Set** the learning rate $\eta$.
3. **Set** the regularization parameters $\lambda$<sub>1</sub>, $\lambda$<sub>2</sub>.
4. **Repeat** until convergence:
   - Compute the gradient:  
     ![image](https://github.com/user-attachments/assets/6d26d97a-d544-451e-bb70-ea4a873a724e)

   - Update \(\beta\):  
     ![image](https://github.com/user-attachments/assets/33389304-5c7e-47fb-9017-13eae1bfc21c)

5. **Stop** when $\beta$<sup>(t)</sup> converges or a maximum number of iterations is reached.

---
