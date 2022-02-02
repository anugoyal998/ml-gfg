# Create Test DataSets using Sklearn
Python’s Sklearn library provides a great sample dataset generator which will help you to create your own custom dataset. It’s fast and very easy to use. Following are the types of samples it provides.
For all the above methods you need to 
`import sklearn.datasets.samples_generator`. 

```
# importing libraries
from sklearn.datasets import make_blobs

# matplotlib for ploting
from matplotlib import pyplot as plt
from matplotlib import style
```

**sklearn.datasets.make_blobs**

```
# Creating Test DataSets using sklearn.datasets.make_blobs
from sklearn.datasets import make_blobs
from matplotlib import pyplot as plt
from matplotlib import style

style.use("fivethirtyeight")

X, y = make_blobs(n_samples = 100, centers = 3,
			cluster_std = 1, n_features = 2)

plt.scatter(X[:, 0], X[:, 1], s = 40, color = 'g')
plt.xlabel("X")
plt.ylabel("Y")

plt.show()
plt.clf()
```

**Output:**

<img src="https://media.geeksforgeeks.org/wp-content/uploads/make_blob.png" >