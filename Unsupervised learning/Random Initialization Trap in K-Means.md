# Random Initialization Trap in K-Means

Random initialization trap is a problem that occurs in the K-means algorithm. In random initialization trap when the centroids of the clusters to be generated are explicitly defined by the User then inconsistency may be created and this may sometimes lead to generating wrong clusters in the dataset. So random initialization trap may sometimes prevent us from developing the correct clusters. 

**Example :**
Suppose you have a dataset with the following points shown in the picture and you want to generate three clusters in this dataset according to their attributes by performing K-means clustering. From the figure, we can get the intuition what are the clusters that are required to be generated. K-means will perform clustering on the basis of the centroids fed into the algorithm and generate the required clusters according to these centroids. 

<img src="https://media.geeksforgeeks.org/wp-content/uploads/20200206014327/rand1.png">

`First Trial`
Suppose we choose 3 sets of centroids according to the figure shown below. The clusters that are generated corresponding to these centroids are shown in the figure below. 

<img src="https://media.geeksforgeeks.org/wp-content/uploads/20200206014758/rand2.png">

Final Model 

<img src="https://media.geeksforgeeks.org/wp-content/uploads/20200206015629/rand3.png">

`Second Trial`
Consider another case in which we choose another set of centroids for the dataset as shown. Now the set of clusters generated will be different from the clusters generated in the previous practice. 

<img src="https://media.geeksforgeeks.org/wp-content/uploads/20200206020039/rand4.png">

Final Model 

<img src="https://media.geeksforgeeks.org/wp-content/uploads/20200206020912/rand5.png">