## **Linear Regression with Gradient Descent**

We aim to model the relationship between \( n \) training examples and \( p \) features (including a bias term) by minimizing the error between predicted and actual target values.

---

### **Step 1: Defining the Model Equation with Error Term**
For each training example *i*, we assume a linear model:  
*y* <sup>i</sup> = *b*<sub>0</sub> + *b*<sub>1</sub> *x*<sub>1</sub> <sup>i</sup> + *b*<sub>2</sub> *x*<sub>2</sub> <sup>i</sup> + .... + *b*<sub>p</sub> *x*<sub>p</sub> <sup>i</sup>

where:
- \( y^{(i)} \) is the actual target value for the \( i \)-th example.
- \( \mathbf{x}^{(i)} = [1, x_1^{(i)}, x_2^{(i)}, \dots, x_p^{(i)}]^T \) is the feature vector (including the bias term).
- \( \mathbf{b} = [b_0, b_1, b_2, \dots, b_p]^T \) is the parameter vector.
- \( \epsilon^{(i)} \) is the error term (residual) for the \( i \)-th example.

The error term \( \epsilon^{(i)} \) captures the difference between the actual and predicted values:

\[
\epsilon^{(i)} = y^{(i)} - \hat{y}^{(i)}
\]

where \( \hat{y}^{(i)} = \mathbf{b}^T \mathbf{x}^{(i)} \) is the predicted value.

For the entire dataset:

\[
\mathbf{y} = X \mathbf{b} + \boldsymbol{\epsilon}
\]

where:
- \( \mathbf{y} \) is an \( n \times 1 \) vector of actual values.
- \( X \) is an \( n \times (p+1) \) feature matrix (including bias).
- \( \boldsymbol{\epsilon} \) is an \( n \times 1 \) vector of error terms.

---

### **Step 2: Defining the Cost Function**
To minimize the overall error, we use the **Mean Squared Error (MSE)** cost function:

\[
J(\mathbf{b}) = \frac{1}{2n} \sum_{i=1}^{n} \epsilon^{(i)2}
\]

Substituting the error term:

\[
J(\mathbf{b}) = \frac{1}{2n} \sum_{i=1}^{n} (y^{(i)} - \mathbf{b}^T \mathbf{x}^{(i)})^2
\]

Or in matrix notation:

\[
J(\mathbf{b}) = \frac{1}{2n} \| \mathbf{y} - X \mathbf{b} \|^2
\]

---

### **Step 3: Computing the Gradient**
To minimize \( J(\mathbf{b}) \), we compute its gradient with respect to each parameter \( b_j \):

\[
\frac{\partial J}{\partial b_j} = -\frac{1}{n} \sum_{i=1}^{n} (y^{(i)} - \mathbf{b}^T \mathbf{x}^{(i)}) x_j^{(i)}
\]

Rewriting in matrix form:

\[
\nabla J(\mathbf{b}) = -\frac{1}{n} X^T (\mathbf{y} - X \mathbf{b})
\]

---

### **Step 4: Gradient Descent Update Rule**
Applying the gradient descent update rule:

\[
\mathbf{b} := \mathbf{b} - \alpha \nabla J(\mathbf{b})
\]

Substituting the gradient:

\[
\mathbf{b} := \mathbf{b} + \alpha \left( \frac{1}{n} X^T (\mathbf{y} - X \mathbf{b}) \right)
\]

For each parameter \( b_j \):

\[
b_j := b_j + \alpha \left( \frac{1}{n} \sum_{i=1}^{n} (y^{(i)} - \mathbf{b}^T \mathbf{x}^{(i)}) x_j^{(i)} \right)
\]

---

### **Step 5: Iterative Optimization**
1. **Initialize** \( \mathbf{b} \) (e.g., zeros or small random values).
2. **Compute the error** \( \boldsymbol{\epsilon} = \mathbf{y} - X \mathbf{b} \).
3. **Calculate the gradient** \( \nabla J(\mathbf{b}) \).
4. **Update** \( \mathbf{b} \) using gradient descent.
5. **Repeat** until convergence (when \( J(\mathbf{b}) \) stabilizes).
