### **1. Overfitting and Underfitting**

**Overfitting** and **underfitting** are two common issues that can occur when training machine learning models, including linear regression. Both refer to how well the model generalizes to unseen data.

#### **Overfitting:**
Overfitting happens when the model learns not only the true underlying relationship in the data but also the noise or random fluctuations. As a result, the model performs very well on the training data but poorly on unseen (test) data because it is too complex and captures unnecessary details.

**Mathematical Explanation:**
For linear regression, the model tries to minimize the **cost function**, which is typically the **Mean Squared Error (MSE)**:

![Capture60](https://github.com/user-attachments/assets/a7bc4f1d-5a01-45b4-b313-1f45a101633c)

where y<sub>i</sub> is the true value and hat y<sub>i</sub>  is the predicted value for the i<sup>th</sup> data point.

In the case of overfitting, the model tries to minimize the error on the training set too much, leading to high variance. This means that the model will have a low training error but a high test error.

**Symptoms of Overfitting:**
   - Low error on the training set but high error on the test set.
   - The model is too complex (too many features or polynomial terms).

#### **Underfitting:**
Underfitting occurs when the model is too simple to capture the underlying pattern in the data. This typically happens when the model has too few parameters or is too constrained.

**Mathematical Explanation:**
In underfitting, the model's cost function (MSE) cannot be minimized effectively because the model is not flexible enough to represent the underlying data distribution. The model's complexity is too low to capture important trends, so it produces high errors both on the training set and the test set.

**Symptoms of Underfitting:**
   - High error on both the training and test sets.
   - The model is too simple (e.g., too few features or linearity when a non-linear relationship exists).

### **2. How Do We Know If the Model is Underfitting or Overfitting?**

To diagnose overfitting or underfitting, we compare the performance of the model on both the **training** and **test** datasets.

- **Overfitting**: The model will have:
  - Low training error
  - High test error
  
- **Underfitting**: The model will have:
  - High training error
  - High test error
  
This is typically assessed using **cross-validation** or by plotting the **learning curve** (error vs. number of training samples) and the **test curve**.

**Mathematical Representation:**
- For overfitting:
  *MSE*<sub>train</sub> << *MSE*<sub>test</sub>
  The model fits the training data very well but performs poorly on unseen data.
  
- For underfitting:
  *MSE*<sub>train</sub> approx sign *MSE*<sub>test</sub> (both high)
  The model does not capture the underlying pattern, leading to poor performance on both datasets.

### **3. Types of Overfitting and Underfitting**

There are different manifestations of overfitting and underfitting, based on how the model complexity and the data interact.

#### **Types of Overfitting:**
   1. **Noise Overfitting**: The model learns random fluctuations in the data (noise) rather than the actual signal. This occurs with too many features or complex polynomial terms that don't generalize well.
   
   2. **Feature Overfitting**: The model becomes overly complex by including too many features. These features might not be relevant to the target variable.
   
   3. **Overfitting Due to Insufficient Regularization**: If regularization is not applied, a high degree polynomial can be learned that fits the training data perfectly, but it fails to generalize.

#### **Types of Underfitting:**
   1. **Simplified Model**: A model that is too simple, such as using linear regression for a problem that requires non-linear modeling (e.g., quadratic or cubic relationships).
   
   2. **Underfitting Due to Regularization**: Over-penalizing the model via **L1 (Lasso)** or **L2 (Ridge)** regularization can lead to underfitting if the regularization term is too large, driving coefficients to near zero.
   
   3. **Insufficient Data**: Using too few features or too little data can cause the model to miss important patterns.

### **4. Techniques to Overcome Overfitting and Underfitting**

#### **Overfitting Solutions:**

1. **Regularization**:
   - **Ridge Regression (L2 Regularization)**: Adds a penalty to the cost function that is proportional to the square of the magnitude of the coefficients:
     \[
     \text{Cost} = \sum_{i=1}^{m} (y_i - \hat{y}_i)^2 + \lambda \sum_{j=1}^{n} b_j^2
     \]
     where \( \lambda \) is the regularization parameter.
     
   - **Lasso Regression (L1 Regularization)**: Adds a penalty to the cost function that is proportional to the absolute value of the coefficients:
     \[
     \text{Cost} = \sum_{i=1}^{m} (y_i - \hat{y}_i)^2 + \lambda \sum_{j=1}^{n} |b_j|
     \]
     Lasso can drive some coefficients to zero, effectively performing feature selection.

2. **Cross-Validation**: Use **k-fold cross-validation** to assess model performance on unseen data. This helps detect overfitting during training and ensures better generalization.

3. **Pruning/Reducing Model Complexity**: Simplify the model by reducing the number of features (feature selection) or using a lower-degree polynomial regression instead of high-degree terms.

4. **Early Stopping**: If you are using gradient descent for optimization, monitor the performance on the validation set and stop training when the validation error begins to rise, even if the training error is still decreasing.

#### **Underfitting Solutions:**

1. **Increase Model Complexity**: Use higher-degree polynomial regression or add more interaction terms between variables to allow the model to capture more complex relationships in the data.

2. **Reduce Regularization**: If you're using Lasso or Ridge regression, try decreasing the regularization parameter \( \lambda \). A very large \( \lambda \) can drive too many coefficients to zero and underfit the data.

3. **Include More Features**: Adding relevant features to the model (e.g., through feature engineering) can help the model capture more information from the data.

4. **Use Non-Linear Models**: If the underlying relationship is non-linear, switch to models like **polynomial regression**, **decision trees**, or **support vector machines**.

### **5. Which Technique is Used in Which Condition?**

- **Overfitting**:
  - Use **regularization** (Ridge or Lasso) to penalize large coefficients.
  - Use **cross-validation** to monitor the model’s ability to generalize.
  - Reduce **model complexity** (e.g., reduce the number of features or polynomial degree).

- **Underfitting**:
  - Increase **model complexity** (e.g., use higher-degree polynomials or more interaction terms).
  - Decrease **regularization** by reducing \( \lambda \).
  - Add more **relevant features** or use **non-linear models** to capture complex relationships.
