The relationship between independent variable and dependent variable is assumed to be linear:
<div align="center">y = mx + c</div>

where *m* is the slope and *c* is the intercept.<br>
The goal of the simple linear regression is to find the best-fit values of *m* and *c* that minimizes the error.
### Error Minimization (Least Squares)
To fit the line, we minimizes the **sum of the squared errors (SSE)**:

![Capture14](https://github.com/user-attachments/assets/63c129d1-37e9-4e8c-9c79-08660939e03b)

where y<sub>i</sub> is the actual value, y^<sub>i</sub> = mx<sub>i</sub> + c is the predicted value, and n is the number of data points.<br>
By minimizing the *SSE*, we can derive the equations of *m* and *c*.
### Deriving the slope (m) and intercept (c)
The formula for m is:

![Capture15](https://github.com/user-attachments/assets/dbc3661b-ddf7-4c25-8307-672eb871cbab)

The formula for c is:

![Capture18](https://github.com/user-attachments/assets/9335ca97-ca98-4a51-9c2e-54d6726390bd)

- Start with SSE:

  ![Capture16](https://github.com/user-attachments/assets/35c4fa91-825a-4ef0-b00d-bf5c2a23aa1c)

- Take the partial derivatives of SSE with respect to m and c, and set them to zero.

![Capture17](https://github.com/user-attachments/assets/fc750fe0-b4f8-43a7-8a8f-50f56000fd5b)

- After solving these equations, you will get the formula for m and c.


