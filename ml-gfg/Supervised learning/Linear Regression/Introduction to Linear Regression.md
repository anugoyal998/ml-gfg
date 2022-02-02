# Introduction to Linear Regression

**Linear Regression** is a machine learning algorithm based on supervised learning. It performs a regression task. Regression models a target prediction value based on independent variables.

<img src="https://media.geeksforgeeks.org/wp-content/uploads/linear-regression-plot.jpg" >

**Hypothesis function for Linear Regression :**

<img src="https://media.geeksforgeeks.org/wp-content/uploads/linear-regression-hypothesis.jpg">

`y = mx + c`

**Cost Function (J):**

<img src="https://media.geeksforgeeks.org/wp-content/uploads/LR-cost-function-2.jpg">

Cost function(J) of Linear Regression is the **Root Mean Squared Error (RMSE)** between predicted y value (pred) and true y value (y).

To update θ1 and θ2 values in order to reduce Cost function (minimizing RMSE value) and achieving the best fit line the model uses Gradient Descent. The idea is to start with random θ1 and θ2 values and then iteratively updating the values, reaching minimum cost.