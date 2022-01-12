# Random Forest Regression in Python

A Random Forest is an ensemble technique capable of performing both regression and classification tasks with the use of multiple decision trees and a technique called Bootstrap and Aggregation, commonly known as bagging. The basic idea behind this is to combine multiple decision trees in determining the final output rather than relying on individual decision trees.

<img src="https://media.geeksforgeeks.org/wp-content/uploads/20200516180708/Capture482.png">

**Example**

Below is a step by step sample implementation of Rando Forest Regression.

Step 1 : Import the required libraries.

```
# Importing the libraries
import numpy as np
import matplotlib.pyplot as plt
import pandas as pd
```

Step 2 : Import and print the dataset

```
data = pd.read_csv('Salaries.csv')
print(data)
```

<img src="https://media.geeksforgeeks.org/wp-content/uploads/20190530103400/Screenshot-1471.png">

Step 3 : Select all rows and column 1 from dataset to x and all rows and column 2 as y

```
x = data.iloc[:, 1:2].values
print(x)
y = data.iloc[:, 2].values
```

Step 4 : Fit Random forest regressor to the dataset

```
# Fitting Random Forest Regression to the dataset
# import the regressor
from sklearn.ensemble import RandomForestRegressor

# create regressor object
regressor = RandomForestRegressor(n_estimators = 100, random_state = 0)

# fit the regressor with x and y data
regressor.fit(x, y)
```

Step 5 : Predicting a new result

```
Y_pred = regressor.predict(np.array([6.5]).reshape(1, 1)) # test the output by changing values
```

Step 6 : Visualising the result

```
# Visualising the Random Forest Regression results

# arange for creating a range of values
# from min value of x to max
# value of x with a difference of 0.01
# between two consecutive values
X_grid = np.arange(min(x), max(x), 0.01)

# reshape for reshaping the data into a len(X_grid)*1 array,
# i.e. to make a column out of the X_grid value				
X_grid = X_grid.reshape((len(X_grid), 1))

# Scatter plot for original data
plt.scatter(x, y, color = 'blue')

# plot predicted data
plt.plot(X_grid, regressor.predict(X_grid),
		color = 'green')
plt.title('Random Forest Regression')
plt.xlabel('Position level')
plt.ylabel('Salary')
plt.show()
```

<img src="https://media.geeksforgeeks.org/wp-content/uploads/20190523104148/Screenshot-3012.png">