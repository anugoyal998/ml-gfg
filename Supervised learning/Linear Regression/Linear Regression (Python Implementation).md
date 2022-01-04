# Linear Regression (Python Implementation)

**Simple Regression**
Let us consider a dataset where we have a value of response y for every feature x: 

<img src="https://media.geeksforgeeks.org/wp-content/uploads/python-linear-regression.png">

A scatter plot of the above dataset looks like:-

<img src="https://media.geeksforgeeks.org/wp-content/uploads/python-linear-regression-1.png">

The equation of regression line is represented as:

<img src="https://www.geeksforgeeks.org/wp-content/ql-cache/quicklatex.com-a38fd0bdce0c76330a46e6d1647ae70c_l3.svg">

```
import numpy as np
import matplotlib.pyplot as plt

def estimate_coef(x, y):
	# number of observations/points
	n = np.size(x)

	# mean of x and y vector
	m_x = np.mean(x)
	m_y = np.mean(y)

	# calculating cross-deviation and deviation about x
	SS_xy = np.sum(y*x) - n*m_y*m_x
	SS_xx = np.sum(x*x) - n*m_x*m_x

	# calculating regression coefficients
	b_1 = SS_xy / SS_xx
	b_0 = m_y - b_1*m_x

	return (b_0, b_1)

def plot_regression_line(x, y, b):
	# plotting the actual points as scatter plot
	plt.scatter(x, y, color = "m",
			marker = "o", s = 30)

	# predicted response vector
	y_pred = b[0] + b[1]*x

	# plotting the regression line
	plt.plot(x, y_pred, color = "g")

	# putting labels
	plt.xlabel('x')
	plt.ylabel('y')

	# function to show plot
	plt.show()

def main():
	# observations / data
	x = np.array([0, 1, 2, 3, 4, 5, 6, 7, 8, 9])
	y = np.array([1, 3, 2, 5, 7, 8, 8, 9, 10, 12])

	# estimating coefficients
	b = estimate_coef(x, y)
	print("Estimated coefficients:\nb_0 = {} \
		\nb_1 = {}".format(b[0], b[1]))

	# plotting regression line
	plot_regression_line(x, y, b)

if __name__ == "__main__":
	main()

```
**Output:**
```
Estimated coefficients:
b_0 = -0.0586206896552
b_1 = 1.45747126437
```

<img src="https://media.geeksforgeeks.org/wp-content/uploads/python-linear-regression-2.png">

**Multiple linear regression**
Multiple linear regression attempts to model the relationship between **two or more features** and a response by fitting a linear equation to the observed data.
Clearly, it is nothing but an extension of simple linear regression.

Consider a dataset with p features(or independent variables) and one response(or dependent variable). 
Also, the dataset contains n rows/observations.
<img src="https://www.geeksforgeeks.org/wp-content/ql-cache/quicklatex.com-92532eb6190045c2217363a7f7e87a25_l3.svg">  <img src="https://www.geeksforgeeks.org/wp-content/ql-cache/quicklatex.com-1fb956c5aaba78500f6cd3cf2936a8c0_l3.svg">
The regression line for p features is represented as: 
<img src="https://www.geeksforgeeks.org/wp-content/ql-cache/quicklatex.com-376902a9d83483528e82e387e94f547f_l3.svg">

```
import matplotlib.pyplot as plt
import numpy as np
from sklearn import datasets, linear_model, metrics

# load the boston dataset
boston = datasets.load_boston(return_X_y=False)

# defining feature matrix(X) and response vector(y)
X = boston.data
y = boston.target

# splitting X and y into training and testing sets
from sklearn.model_selection import train_test_split
X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.4,
													random_state=1)

# create linear regression object
reg = linear_model.LinearRegression()

# train the model using the training sets
reg.fit(X_train, y_train)

# regression coefficients
print('Coefficients: ', reg.coef_)

# variance score: 1 means perfect prediction
print('Variance score: {}'.format(reg.score(X_test, y_test)))

# plot for residual error

## setting plot style
plt.style.use('fivethirtyeight')

## plotting residual errors in training data
plt.scatter(reg.predict(X_train), reg.predict(X_train) - y_train,
			color = "green", s = 10, label = 'Train data')

## plotting residual errors in test data
plt.scatter(reg.predict(X_test), reg.predict(X_test) - y_test,
			color = "blue", s = 10, label = 'Test data')

## plotting line for zero residual error
plt.hlines(y = 0, xmin = 0, xmax = 50, linewidth = 2)

## plotting legend
plt.legend(loc = 'upper right')

## plot title
plt.title("Residual errors")

## method call for showing the plot
plt.show()

```

**Output:**

```
Coefficients:
[ -8.80740828e-02   6.72507352e-02   5.10280463e-02   2.18879172e+00
-1.72283734e+01   3.62985243e+00   2.13933641e-03  -1.36531300e+00
2.88788067e-01  -1.22618657e-02  -8.36014969e-01   9.53058061e-03
-5.05036163e-01]
Variance score: 0.720898784611
```

<img src="https://media.geeksforgeeks.org/wp-content/uploads/python-linear-regression-3.png">

**Assumptions:**
Given below are the basic assumptions that a linear regression model makes regarding a dataset on which it is applied:  
* `Linear relationship`: Relationship between response and feature variables should be linear. The linearity assumption can be tested using scatter plots.
<img src="https://media.geeksforgeeks.org/wp-content/uploads/python-linear-regression-4.png">
* `Little or no multi-collinearity`: It is assumed that there is little or no multicollinearity in the data. Multicollinearity occurs when the features (or independent variables) are not independent of each other.