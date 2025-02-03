### **1. Error-based Metrics**

- **Mean Absolute Error (MAE)**  
  Formula:  
  ![image](https://github.com/user-attachments/assets/513bae33-99c6-4503-a049-2f0e950c0358)

  - Measures the average absolute difference between actual and predicted values.

- **Mean Squared Error (MSE)**  
  Formula:  
  ![image](https://github.com/user-attachments/assets/b5b5f297-0196-4a9a-a973-8cb5b65b4941)

  - Penalizes larger errors more heavily.

- **Root Mean Squared Error (RMSE)**  
  Formula:  
  ![image](https://github.com/user-attachments/assets/93b0e9f7-050f-4ced-a946-9defc09b0f89)

  - Gives a result in the same units as the target variable.

- **Mean Squared Logarithmic Error (MSLE)**  
  Formula:  
  ![image](https://github.com/user-attachments/assets/3df508ab-76ab-4540-bf1e-b2fbb09f1a46)

  - Suitable for cases where the data grows exponentially.

- **Huber Loss**  
  Formula:  
  ![image](https://github.com/user-attachments/assets/4962e51d-133e-45a3-bb83-cd4d71d55944)

  where \( a = y_i - \hat{y}_i \).  
  - A combination of MSE and MAE, robust to outliers.

- **Log-Cosh Loss**  
  Formula:  
  ![image](https://github.com/user-attachments/assets/2896308e-dc24-47ed-a05c-603fafd02fb0)

  - A smooth approximation of the absolute error that is less sensitive to outliers.

---

### **2. Goodness-of-Fit Metrics**

- **Coefficient of Determination (\( R^2 \))**  
  Formula:  
  ![image](https://github.com/user-attachments/assets/b74f48a8-bfa4-4cd0-9562-fa6aa45fe9fa)

  - Represents the proportion of variance explained by the model.

- **Adjusted \( R^2 \)**  
  Formula:  
  ![image](https://github.com/user-attachments/assets/e2c8bd9d-c780-4279-b527-8ed89e248428)

  - Adjusted for the number of predictors, penalizing the use of irrelevant features.

- **Explained Variance Score**  
  Formula:  
 ![image](https://github.com/user-attachments/assets/21c57324-ddd9-44c7-91dc-b3b05523fe4d)

  - Measures how well the variance in the predictions is explained by the model.

- **F-statistic**  
  Formula:  
  ![image](https://github.com/user-attachments/assets/98bd563d-1f13-42d4-bd9f-9162cf4f8e25)

  - Used to test if the model's predictors are significantly better than a baseline model.

---

### **3. Relative Error Metrics**

- **Mean Absolute Percentage Error (MAPE)**  
  Formula:  
  ![image](https://github.com/user-attachments/assets/92f20f57-22f4-442b-903d-e66f6e552899)

  - Expresses error as a percentage of the actual values.

- **Symmetric Mean Absolute Percentage Error (SMAPE)**  
  Formula:  
  ![image](https://github.com/user-attachments/assets/a0a1787b-9c36-49ed-b3f9-5d00176e1b66)

  - A symmetric version of MAPE that works better for small values.

- **Mean Absolute Scaled Error (MASE)**  
  Formula:  
  ![image](https://github.com/user-attachments/assets/6d750442-aa72-4033-9d8d-875718a071bc)

  - Helps compare models across different datasets and baselines.

---

### **4. Other Useful Metrics**

- **Theil’s U-statistic (U-statistic)**  
  Formula:  
  ![image](https://github.com/user-attachments/assets/6d5fdeb9-806f-4a51-9b78-9899e2e5d834)

  - A metric that measures the relative accuracy of predictions in comparison to the observed values.

- **Cumulative Gain (CG)**  
  Formula:  
  ![image](https://github.com/user-attachments/assets/9ffd9e17-0fb9-46bc-aecd-adcdf63104fb)

  - Measures the cumulative predicted value.

- **Precision and Recall** (in case of regression tasks with classification thresholds)  
  - These metrics are often more commonly used in classification tasks, but can be adapted for regression in the context of thresholded predictions.

---

### **5. Specialized Metrics for Certain Regression Tasks**

- **Quantile Loss**  
  Formula:  
  ![image](https://github.com/user-attachments/assets/ecb30f91-e104-405b-beac-1db4d0c5418f)

  where \( \rho_\tau (u) = u(\tau - I(u < 0)) \).  
  - Used in quantile regression for predicting different quantiles of the target distribution.

- **Mean Absolute Error per Example (MAE/Ex)**  
  Formula:  
  ![image](https://github.com/user-attachments/assets/065b36eb-cc11-45ba-bb88-81f4d4452cf4)

  - Measures average per-feature error.

---

### **6. Model Performance Metrics**

- **Bias-Variance Decomposition**  
  - While not a direct metric, this is useful for understanding how bias and variance affect model performance.  
  ![image](https://github.com/user-attachments/assets/c2f68834-5cff-4127-ada3-71e3cb078334)

  - Provides insight into how well the model is generalizing.

---
