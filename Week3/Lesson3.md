## Logistic regression

### Sigmoid function for classification

The sigmoid function is defined as: g(z) = 1/ (1 + e^-z). This function will always return a value between 0 and 1. If z is very large, then g(z) will be close to 1. If z is very small, then g(z) will be close to 0. If z = 0, then g(z) = 0.5.

This gives us the probability of the output being 1. If the probability is greater than 0.5, then we predict 1, otherwise we predict 0. Ie. if z >= 0, then y = 1, else y = 0. And z is just the linear regression function:
z = w1x1 + w2x2 + ... + wnxn + b.

### Decision boundary

This gives us the ability to create a boundary of 0 and 1 in multidimensional input spaces:

Notice how, if w1, and w2 are 1, it creates the following function relating x1 and x2. If instead w1 where 2, we would have x2 = -2x1 + 3.

![img](./Screenshot%202023-05-24%20162240.png)

### Non-linear decision boundaries

We need to create a ellipsoid function, so get the squared values.

The more features to higher powers we add, the more complex equations:

![img](./Screenshot%202023-05-24%20163405.png)

### Cost function

The base cost function we use is only convex for our basic wx + b hypotheis its a parabola that we slowly walk down. The problem with the sigmoid function is that, using the squared error cost function we get a lot of local minimas. Instead we use the following cost function:

![img](./Screenshot%202023-05-24%20164722.png)

since f(x) the hypotheis is between 0, 1. As its the output of the sigmoid function.

- -log(f(x)) -> is 0 when f(x) = 1 (no error) and infinite at 0 (maximum error)

- -log(1 - f(x)) -> is 0 when f(x) = 0 (no error) and infinite at 1 (maximum error).

We needed this because we only went from 0 and 1, so we didn't properly penalize errors of 1, which are maximum possible error.

### Simplified cost function

![](./Screenshot%202023-05-24%20170421.png)

![](./Screenshot%202023-05-24%20174249.png)

## Fitting problems

You can see in the first example, that we just don't fit well at all, we have a high bias. In the second example, we have a generalazied hypothesis, it will work for our data, and other new data. In the third example, we have a high variance, we are overfitting our data, and will not generalize well to new data, as we built our model to only just fit our data.

![](./Screenshot%202023-05-24%20175051.png)

The same can be said for the classification problem. The right one is just given too many features, and is trying so hard to fit the two outlier benign tumors.

![](./Screenshot%202023-05-24%20175454.png)

## Regularization

We regularize the data to stop overfitting, when we have high power terms, it can warp the fit so that it perfectly fits our outlier terms. Giving a penalty for any large values (warping) of ws, we can stop this from happening. However, it can force underfitting if we regularize too much.

![](./Screenshot%202023-05-24%20190245.png)

This regularization term can also be added for classification problems. And when you take a partial derivative with respedc to wj, you only get the wj term.

ie. regular derivative + `lambda/m * wj`
