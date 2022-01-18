# K means Clustering – Introduction

We are given a data set of items, with certain features, and values for these features (like a vector). The task is to categorize those items into groups. To achieve this, we will use the kMeans algorithm; an unsupervised learning algorithm. 
(It will help if you think of items as points in an n-dimensional space).  The algorithm will categorize the items into k groups of similarity. To calculate that similarity, we will use the euclidean distance as measurement.

**The algorithm works as follows:**
* First, we initialize k points, called means, randomly.
* We categorize each item to its closest mean and we update the mean’s coordinates, which are the averages of the items categorized in that mean so far.
* We repeat the process for a given number of iterations and at the end, we have our clusters.

        Initialize k means with random values

        For a given number of iterations:
            Iterate through items:
                Find the mean closest to the item
                Assign item to mean
                Update mean

**ReadData**
```
def ReadData(fileName):

	# Read the file, splitting by lines
	f = open(fileName, 'r');
	lines = f.read().splitlines();
	f.close();

	items = [];

	for i in range(1, len(lines)):
		line = lines[i].split(',');
		itemFeatures = [];

		for j in range(len(line)-1):
			
			# Convert feature value to float
			v = float(line[j]);
			
			# Add feature value to dict
			itemFeatures.append(v);

		items.append(itemFeatures);

	shuffle(items);

	return items;
```

**Initialize Means**
We want to initialize each mean’s values in the range of the feature values of the items. For that, we need to find the min and max for each feature. 
```
def FindColMinMax(items):
	n = len(items[0]);
	minima = [sys.maxint for i in range(n)];
	maxima = [-sys.maxint -1 for i in range(n)];
	
	for item in items:
		for f in range(len(item)):
			if (item[f] < minima[f]):
				minima[f] = item[f];
			
			if (item[f] > maxima[f]):
				maxima[f] = item[f];

return minima,maxima;
```

We initialize each mean’s feature values randomly between the corresponding minimum and maximum in those above two lists:

```
def InitializeMeans(items, k, cMin, cMax):

	# Initialize means to random numbers between
	# the min and max of each column/feature
	f = len(items[0]); # number of features
	means = [[0 for i in range(f)] for j in range(k)];
	
	for mean in means:
		for i in range(len(mean)):

			# Set value to a random float
			# (adding +-1 to avoid a wide placement of a mean)
			mean[i] = uniform(cMin[i]+1, cMax[i]-1);

	return means;
```

```
def EuclideanDistance(x, y):
	S = 0; # The sum of the squared differences of the elements
	for i in range(len(x)):
		S += math.pow(x[i]-y[i], 2)

	#The square root of the sum
	return math.sqrt(S)
```

**Update Means**
To update a mean, we need to find the average value for its feature, for all the items in the mean/cluster. We can do this by adding all the values and then dividing by the number of items, or we can use a more elegant solution. We will calculate the new average without having to re-add all the values, by doing the following: 

    m = (m*(n-1)+x)/n}

where m is the mean value for a feature, n is the number of items in the cluster, and x is the feature value for the added item. We do the above for each feature to get the new mean.

```
def UpdateMean(n,mean,item):
	for i in range(len(mean)):
		m = mean[i];
		m = (m*(n-1)+item[i])/float(n);
		mean[i] = round(m, 3);
	
	return mean;
```

**Classify Items**

```
def Classify(means,item):

	# Classify item to the mean with minimum distance
	minimum = sys.maxint;
	index = -1;

	for i in range(len(means)):

		# Find distance from item to mean
		dis = EuclideanDistance(item, means[i]);

		if (dis < minimum):
			minimum = dis;
			index = i;
	
	return index;
```

**Find Means**
```
def CalculateMeans(k,items,maxIterations=100000):

	# Find the minima and maxima for columns
	cMin, cMax = FindColMinMax(items);
	
	# Initialize means at random points
	means = InitializeMeans(items,k,cMin,cMax);
	
	# Initialize clusters, the array to hold
	# the number of items in a class
	clusterSizes= [0 for i in range(len(means))];

	# An array to hold the cluster an item is in
	belongsTo = [0 for i in range(len(items))];

	# Calculate means
	for e in range(maxIterations):

		# If no change of cluster occurs, halt
		noChange = True;
		for i in range(len(items)):

			item = items[i];

			# Classify item into a cluster and update the
			# corresponding means.	
			index = Classify(means,item);

			clusterSizes[index] += 1;
			cSize = clusterSizes[index];
			means[index] = UpdateMean(cSize,means[index],item);

			# Item changed cluster
			if(index != belongsTo[i]):
				noChange = False;

			belongsTo[i] = index;

		# Nothing changed, return
		if (noChange):
			break;

	return means;
```

**Find Clusters**
```
def FindClusters(means,items):
	clusters = [[] for i in range(len(means))]; # Init clusters
	
	for item in items:

		# Classify item into a cluster
		index = Classify(means,item);

		# Add item to cluster
		clusters[index].append(item);

	return clusters;
```

