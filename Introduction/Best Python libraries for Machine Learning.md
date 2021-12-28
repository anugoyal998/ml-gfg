# Best Python libraries for Machine Learning

* Numpy
* Scipy
* Scikit-learn
* Theano
* TensorFlow
* Keras
* PyTorch
* Pandas
* Matplotlib

<img src="https://media.geeksforgeeks.org/wp-content/uploads/image5-1.jpeg" >

**NumPy** is a very popular python library for large multi-dimensional array and matrix processing, with the help of a large collection of high-level mathematical functions. It is very useful for fundamental scientific computations in Machine Learning. It is particularly useful for **linear algebra, Fourier transform, and random number capabilities**. High-end libraries like **TensorFlow** uses **NumPy** internally for manipulation of Tensors. 

```
# Python program using NumPy
# for some basic mathematical
# operations
 
import numpy as np
 
# Creating two arrays of rank 2
x = np.array([[1, 2], [3, 4]])
y = np.array([[5, 6], [7, 8]])
 
# Creating two arrays of rank 1
v = np.array([9, 10])
w = np.array([11, 12])
 
# Inner product of vectors
print(np.dot(v, w), "\n")
 
# Matrix and Vector product
print(np.dot(x, v), "\n")
 
# Matrix and matrix product
print(np.dot(x, y))
```

**Output:** 
```
219 

[29 67] 

[[19 22]
[43 50]]
```

<img src="https://media.geeksforgeeks.org/wp-content/uploads/image6.png" >

**SciPy** is a very popular library among Machine Learning enthusiasts as it contains different modules for **optimization, linear algebra, integration and statistics**. There is a difference between the **SciPy library** and the **SciPy stack**. The SciPy is one of the core packages that make up the SciPy stack. SciPy is also very useful for image manipulation. 

```
# Python script using Scipy
# for image manipulation

from scipy.misc import imread, imsave, imresize

# Read a JPEG image into a numpy array
img = imread('D:/Programs / cat.jpg') # path of the image
print(img.dtype, img.shape)

# Tinting the image
img_tint = img * [1, 0.45, 0.3]

# Saving the tinted image
imsave('D:/Programs / cat_tinted.jpg', img_tint)

# Resizing the tinted image to be 300 x 300 pixels
img_tint_resize = imresize(img_tint, (300, 300))

# Saving the resized tinted image
imsave('D:/Programs / cat_tinted_resized.jpg', img_tint_resize)
```

**Original image:**

<img src="https://media.geeksforgeeks.org/wp-content/uploads/cat-1-1-300x240.jpg" >

**Tinted image:**

<img src="https://media.geeksforgeeks.org/wp-content/uploads/image15-300x240.jpg">

**Resized tinted image:**

<img src="https://media.geeksforgeeks.org/wp-content/uploads/cat_tinted_resized-1.jpg">  

#
<img src="https://media.geeksforgeeks.org/wp-content/uploads/image7-1.png">

**Skikit-learn** is one of the most popular ML libraries for classical ML algorithms. It is built on top of two basic Python libraries, viz., **NumPy and SciPy**. Scikit-learn supports most of the supervised and unsupervised learning algorithms. Scikit-learn can also be used for data-mining and data-analysis, which makes it a great tool who is starting out with ML. 

```
# Python script using Scikit-learn
# for Decision Tree Classifier

# Sample Decision Tree Classifier
from sklearn import datasets
from sklearn import metrics
from sklearn.tree import DecisionTreeClassifier

# load the iris datasets
dataset = datasets.load_iris()

# fit a CART model to the data
model = DecisionTreeClassifier()
model.fit(dataset.data, dataset.target)
print(model)

# make predictions
expected = dataset.target
predicted = model.predict(dataset.data)

# summarize the fit of the model
print(metrics.classification_report(expected, predicted))
print(metrics.confusion_matrix(expected, predicted))
```

**Output:**

```
DecisionTreeClassifier(class_weight=None, criterion='gini', max_depth=None,
            max_features=None, max_leaf_nodes=None,
            min_impurity_decrease=0.0, min_impurity_split=None,
            min_samples_leaf=1, min_samples_split=2,
            min_weight_fraction_leaf=0.0, presort=False, random_state=None,
            splitter='best')
              precision    recall  f1-score   support

           0       1.00      1.00      1.00        50
           1       1.00      1.00      1.00        50
           2       1.00      1.00      1.00        50

   micro avg       1.00      1.00      1.00       150
   macro avg       1.00      1.00      1.00       150
weighted avg       1.00      1.00      1.00       150

[[50  0  0]
 [ 0 50  0]
 [ 0  0 50]]
```

For more details about libraries refer to [this](https://www.geeksforgeeks.org/best-python-libraries-for-machine-learning/) article
 
