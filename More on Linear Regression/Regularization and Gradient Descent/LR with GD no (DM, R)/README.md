## **Linear Regression with Gradient Descent**

We aim to model the relationship between \( n \) training examples and \( p \) features (including a bias term) by minimizing the error between predicted and actual target values.

---

### **Step 1: Defining the Model Equation with Error Term**
For each training example *i*, we assume a linear model:  
*y* <sup>i</sup> = *b*<sub>0</sub> + *b*<sub>1</sub> *x*<sub>1</sub> <sup>i</sup> + *b*<sub>2</sub> *x*<sub>2</sub> <sup>i</sup> + .... + *b*<sub>p</sub> *x*<sub>p</sub> <sup>i</sup> + $\epsilon$ <sup>i</sup>

or in vector notation:  
*y* <sup>i</sup> = **b** <sup>T</sup> **X**<sup>i</sup> + $\epsilon$


where:
- *y* <sup>i</sup> is the actual target value for the \( i \)-th example.
- **X**<sup>i</sup> = [1, *x*<sub>1</sub> <sup>i</sup>, *x*<sub>2</sub> <sup>i</sup>, ....., *x*<sub>p</sub> <sup>i</sup>]<sup>T</sup> is the feature vector (including the bias term).
- **b** = [*b*<sub>0</sub>, *b*<sub>1</sub>, *b*<sub>2</sub>, ...., *b*<sub>p</sub>]<sup>T</sup> is the parameter vector.
- $\epsilon$ <sup>i</sup> is the error term (residual) for the \( i \)-th example.

The error term $\epsilon$ <sup>i</sup> captures the difference between the actual and predicted values.


For the entire dataset:

where:
- **y** is an *n* X 1 vector of actual values.
- **X** is an *n* X (*p* + 1) feature matrix (including bias).
- $\epsilon$ <sup>i</sup> is an *n* X 1 vector of error terms.
---

### **Step 2: Defining the Cost Function**
To minimize the overall error, we use the **Mean Squared Error (MSE)** cost function:

![image](https://github.com/user-attachments/assets/f17fa658-3adb-4970-b5f6-ba15ec8bdb5d)



Substituting the error term:

![image](https://github.com/user-attachments/assets/415cc651-1ba6-4b2a-9366-c61e44aeeea4)


Or in matrix notation:

![image](https://github.com/user-attachments/assets/3740757d-09e6-4715-a461-6af10e97d019)


---

### **Step 3: Computing the Gradient**
To minimize \( J(\mathbf{b}) \), we compute its gradient with respect to each parameter \( b_j \):

![image](https://github.com/user-attachments/assets/86286412-cb30-40c1-b170-cb6b561a5ed0)


Rewriting in matrix form:

![image](https://github.com/user-attachments/assets/ed210b50-7d4f-45bb-8346-e2594c39b8f1)


---

### **Step 4: Gradient Descent Update Rule**
Applying the gradient descent update rule:

![image](https://github.com/user-attachments/assets/5bb33976-07a9-4ba6-afd5-cbcf7eb1481e)


Substituting the gradient:

![image](https://github.com/user-attachments/assets/fc14d229-b894-4d08-98f5-6351f8304d13)


For each parameter \( b_j \):

![image](https://github.com/user-attachments/assets/6b159958-3a98-4d57-b349-de23e483aa91)

---

### **Step 5: Iterative Optimization**
1. **Initialize** **b** (e.g., zeros or small random values).
2. **Compute the error** $\epsilon$ = **y** - **X** **b**.
3. **Calculate the gradient** (**J**(**b**)).
4. **Update** **b** using gradient descent.
5. **Repeat** until convergence (when **J**(**b**) stabilizes).
