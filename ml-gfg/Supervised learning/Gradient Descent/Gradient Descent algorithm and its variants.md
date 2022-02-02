# Gradient Descent algorithm and its variants

Gradient Descent is an optimization algorithm used for minimizing the cost function in various machine learning algorithms.

**Types of gradient Descent:**

* `Batch Gradient Descent`: This is a type of gradient descent which processes all the training examples for each iteration of gradient descent. But if the number of training examples is large, then batch gradient descent is computationally very expensive. Hence if the number of training examples is large, then batch gradient descent is not preferred. Instead, we prefer to use stochastic gradient descent or mini-batch gradient descent.
* `Stochastic Gradient Descent`: This is a type of gradient descent which processes 1 training example per iteration. Hence, the parameters are being updated even after one iteration in which only a single example has been processed. Hence this is quite faster than batch gradient descent. But again, when the number of training examples is large, even then it processes only one example which can be additional overhead for the system as the number of iterations will be quite large.
* `Mini Batch gradient descent`: This is a type of gradient descent which works faster than both batch gradient descent and stochastic gradient descent. Here b examples where b<m are processed per iteration. So even if the number of training examples is large, it is processed in batches of b training examples in one go. Thus, it works for larger training examples and that too with lesser number of iterations.


Let m be the number of training examples.
Let n be the number of features.

**Algorithm for batch gradient descent :**
Let hθ(x) be the hypothesis for linear regression. Then, the cost function is given by:
Let Σ represents the sum of all training examples from i=1 to m.
```
Jtrain(θ) = (1/2m) Σ( hθ(x(i))  - y(i))2

Repeat {
 θj = θj – (learning rate/m) * Σ( hθ(x(i))  - y(i))xj(i)
    For every j =0 …n 
}
```

**Algorithm for stochastic gradient descent:**
```
Hence,
Let (x(i),y(i)) be the training example
Cost(θ, (x(i),y(i))) = (1/2) Σ( hθ(x(i))  - y(i))2

Jtrain(θ) = (1/m) Σ Cost(θ, (x(i),y(i)))

Repeat {

For i=1 to m{

         θj = θj – (learning rate) * Σ( hθ(x(i))  - y(i))xj(i)
        For every j =0 …n

                } 
}
```

**Algorithm for mini batch gradient descent:**
Say b be the no of examples in one batch, where b < m.
Assume b = 10, m = 100;

**Note**: However we can adjust the batch size. It is generally kept as power of 2. The reason behind it is because some hardware such as GPUs achieve better run 
time with common batch sizes such as power of 2.
```
Repeat {
 For i=1,11, 21,…..,91

    Let Σ be the summation from i to i+9 represented by k. 

    θj = θj – (learning rate/size of (b) ) * Σ( hθ(x(k))  - y(k))xj(k)
        For every j =0 …n

}
```