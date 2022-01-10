# Decision Tree Introduction with example

<img src="https://media.geeksforgeeks.org/wp-content/uploads/dcsion.png">

In Decision Tree the major challenge is to identification of the attribute for the root node in each level. This process is known as attribute selection. We have two popular attribute selection measures:
* Information Gain
* Gini Index

`Information Gain`: When we use a node in a decision tree to partition the training instances into smaller subsets the entropy changes. Information gain is a measure of this change in entropy.

**Building Decision Tree using Information Gain**
**The essentials:**
* Start with all training instances associated with the root node
* Use info gain to choose which attribute to label each node with
* Note: No root-to-leaf path should contain the same discrete attribute twice
* Recursively construct each subtree on the subset of training instances that would be classified down that path in the tree.

**The border cases:**
* If all positive or all negative training instances remain, label that node “yes” or “no” accordingly
* If no attributes remain, label with a majority vote of training instances left at that node
* If no instances remain, label with a majority vote of the parent’s training instances

**Example:**
Now, lets draw a Decision Tree for the following data using Information gain.

Training set: 3 features and 2 classes
| X | Y | Z | C |
| 1 | 1 | 1 | 1 |
| 1 | 1 | 0 | 1 |
| 0 | 0 | 1 | 2 |
| 1 | 0 | 0 | 2 |

<img src="https://media.geeksforgeeks.org/wp-content/uploads/tr4.png">

<img src="https://media.geeksforgeeks.org/wp-content/cdn-uploads/20210317184559/y-attribute.png">

<img src="https://media.geeksforgeeks.org/wp-content/cdn-uploads/20210317184631/z-attribute.png">


From the above images we can see that the information gain is maximum when we make a split on feature Y. So, for the root node best suited feature is feature Y. Now we can see that while splitting the dataset by feature Y, the child contains pure subset of the target variable. So we don’t need to further split the dataset.

The final tree for the above dataset would be look like this:

<img src="https://media.geeksforgeeks.org/wp-content/uploads/tr6.png">

`Gini Index`
* Gini Index is a metric to measure how often a randomly chosen element would be incorrectly identified.
* It means an attribute with lower Gini index should be preferred.
* Sklearn supports “Gini” criteria for Gini Index and by default, it takes “gini” value.
* The Formula for the calculation of the of the Gini Index is given below.
<img src="https://www.geeksforgeeks.org/wp-content/ql-cache/quicklatex.com-d0d96c305b893bd453f1160f0cbc7b67_l3.svg">

**Example:**

Index	A	B	C	D	E
1	4.8	3.4	1.9	0.2	positive
2	5	3	1.6	1.2	positive
3	5	3.4	1.6	0.2	positive
4	5.2	3.5	1.5	0.2	positive
5	5.2	3.4	1.4	0.2	positive
6	4.7	3.2	1.6	0.2	positive
7	4.8	3.1	1.6	0.2	positive
8	5.4	3.4	1.5	0.4	positive
9	7	3.2	4.7	1.4	negative
10	6.4	3.2	4.7	1.5	negative
11	6.9	3.1	4.9	1.5	negative
12	5.5	2.3	4	1.3	negative
13	6.5	2.8	4.6	1.5	negative
14	5.7	2.8	4.5	1.3	negative
15	6.3	3.3	4.7	1.6	negative
16	4.9	2.4	3.3	1	negative

In Gini Index, we have to choose some random values to categorize each attribute. These values for this dataset are:

    A       B        C         D
    >= 5     >= 3.0      >= 4.2    >= 1.4
    < 5      < 3.0       < 4.2     < 1.4

    Positive    Negative
    For A|>= 5.0    5       7
        |<5    3       1
    Ginin Index of A = 0.45825    

    Positive    Negative
    For B|>= 3.0    8       4
        |< 3.0    0       4
    Gini Index of B= 0.3345

    Positive    Negative
    For C|>= 4.2    0       6
        |< 4.2    8       2
    Gini Index of C= 0.2   

    Positive    Negative
    For D|>= 1.4    0       5
        |< 1.4    8       3
    Gini Index of D= 0.273

<img src="https://media.geeksforgeeks.org/wp-content/uploads/qa.png">