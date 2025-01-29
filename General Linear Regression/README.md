## Multiple Linear Regression for *n* Independent Variables and One Dependent Variable
For a dataset with *n* independent variables and one dependent variable, the multiple linear regression model is given by:  
*y* = b<sub>0</sub> + b<sub>1</sub>x<sub>1</sub> + b<sub>2</sub>x<sub>2</sub> + ..... + b<sub>n</sub>x<sub>n</sub> + $\epsilon$ 

where:
- *y* is the dependent variable.
- x<sub>1</sub>, x<sub>2</sub>, ..... x<sub>n</sub> are independent variables.
- b<sub>0</sub>, b<sub>1</sub>, b<sub>2</sub>, ...... b<sub>n</sub> are regression coefficients.
- $\epsilon$  is the error term.

**Step 1**: **Matrix Representation**
We represent the system in matrix form
*Y* = *X* *B* + *E*

where:
- *Y* is the *m* x 1 column vector of dependent variables:
  
  ![Capture40](https://github.com/user-attachments/assets/1d84592c-931f-44e8-847a-d8df6df209fe)

- *X* is the *m* x (n + 1) matrix of independent variables (with a column of ones for b<sub>0</sub>)
  
  ![Capture41](https://github.com/user-attachments/assets/5fc54a56-3d27-4e5b-bc2a-3f8cf9f13231)

- *B* is the(n + 1) x 1 vector of regression coefficients:
  
  ![Capture42](https://github.com/user-attachments/assets/8fa374e1-21ff-4964-891e-de9e9067b654)

- *E* is the *m* x 1 error vector:
  
  ![Capture43](https://github.com/user-attachments/assets/af918f4a-54a0-4dfd-b6b1-c612403dbef1)

**Step 2: Normal Equation**
TO find the best-fit coefficients, we minimizes the sum of squared errors:

![Capture45](https://github.com/user-attachments/assets/c07fdc7d-5699-43c6-bfae-dbd81a53e36e)

Taking the derivative with respect to *B* and setting it to zero:

![Capture44](https://github.com/user-attachments/assets/944cd76f-a5ad-49ad-be8e-55dc3600fce5)

Solving:

![Capture46](https://github.com/user-attachments/assets/32949b11-e972-4b53-aae9-440b2c835dd4)

**Step 3: Solving for B**

If X<sup>T</sup>X is invertible, we solve for *B*:

![Capture47](https://github.com/user-attachments/assets/e7864713-7bc1-44c7-add6-c19a748db1f1)

This equation provides the optima regression coefficients using the least squares method.


##

- In case of one independent variable and one dependent variable, the graph will be a straight line in 2-D.
- In case of two independent variable and one dependent variable, the graph will be a plane in 3-D.


  
