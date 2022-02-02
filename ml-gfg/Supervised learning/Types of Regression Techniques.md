# Types of Regression Techniques

A simple linear regression code

```
# importing libraries
import numpy as np
import matplotlib.pyplot as plt
from sklearn.linear_model import LinearRegression

x = 11 * np.random.random((10, 1))

# y = a * x + b
y = 1.0 * x + 3.0

# create a linear regression model
model = LinearRegression()
model.fit(x, y)

# predict y from the data where the x is predicted from the x
x_pred = np.linspace(0, 11, 100)
y_pred = model.predict(x_pred[:, np.newaxis])

# plot the results
plt.figure(figsize =(3, 5))
ax = plt.axes()
ax.scatter(x, y)

ax.plot(x_pred, y_pred)
ax.set_xlabel('predictors')
ax.set_ylabel('criterion')
ax.axis('tight')

plt.show()
```

<img src="https://media.geeksforgeeks.org/wp-content/uploads/linear_reg.png" >