## Supervised Linear regression, multiple features.

Naming Convention:

![img](./Screenshot%202023-05-22%20225949.png)

![img](.//Screenshot%202023-05-22%20230147.png)

Now, f(x) = w1x1 + w2x2 + w3x3 + ... + wnxn + b.
Each feature represents something else, such as in the house example:

- size
- number of bedrooms
- number of floors
- age of home

A way to get the perfect weights is to use the **Normal Equation**. This only works for linear regression, and is very computationally expensive for large datasets.

### Feature Scaling

Feature scaling is a technique to allow gradient descent to follow a much more direct path, because the features are all on the same scale. This is done by subtracting the mean from each feature, and dividing by the range (or standard deviation). This is also called **mean normalization**. If we didn't do this, the gradient descent algorithm would take a long time to converge, as a small change in one feature would cause a large change in the hypothesis, and a large change in the other features would cause a small change in the hypothesis.

![img](./Screenshot%202023-05-22%20232938.png)

Scaling should go from about -1 to 1, or -3 to 3. If the range is much larger than that, then the gradient descent algorithm will take a long time to converge. The important thing is that all the features are on roughly the same scale.

### How to check if gradient descent is working correctly

It is really easy to check with a graph of the cost function. With each iteration it should be decreasing. Otherwise, there is a problem with the learning rate, or bug in the code.

For example a graph like this:
![img](./Screenshot%202023-05-22%20233845.png)

Automatic conversion tests are dangerous, becuase they might stop you in a flat part of the cost function, but there is a minimum later.

### Choosing the learning rate

If the cost function ever ticks up, then the learning rate is too large. If the cost function is decreasing very slowly, then the learning rate is too small.

## Feature Engineering (using data to make new features)

An example can be when calculating the price of a house, you have its data on length and width, but maybe it is more useful to have the Area, so you add another feature **x3 = x1\*x2**.

### Polynomial engineering

You can instead set another feature size squared, as you notice that the size matters less and less as it grows. **x4 = x3\*x3**. This will now make your fit a quadratic, similarly you can have a square root function or more.

**NOTICE:** Feature scaling is super important because the square is a much larger range than its original value.
