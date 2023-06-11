## Training networks overview

### Compare logistic regression and neural networks

First see how it is the same steps as the logistic regression problem.
![](./Screenshot%202023-05-31%20192526.png)

### Deep dive on creating the model

We define the model and how to evaluate the inputs using forward propagation.
![](./Screenshot%202023-05-31%20192718.png)

### Define the loss function

The loss function in the neural network is actually the same as in our logistic regression problem. loss = -ylog(y_hat) - (1-y)log(1-y_hat), because our answer is true or false, so we can use the same loss function.

In TensorFlow, we call is binary cross entropy loss.

![](./Screenshot%202023-05-31%20193100.png)

If instead we had a linear regression problem:

![](./Screenshot%202023-05-31%20193140.png)

### Cost function

The cost function is also the same, just using our new loss function and the tensor of weights and matrix of biases.

![](./Screenshot%202023-05-31%20193324.png)

## Backpropagation

**This is the hard part**

### Activation functions

We learnt about the ReLU function, used when features should range more than just between 0 and 1.

![](./Screenshot%202023-05-31%20194021.png)

** CHOOSING ACTIVATION FUNCTIONS **

- Regression problem: Use a linear activation function
- Binary classification problem: Use sigmoid activation function
- Multi-class classification problem: Use softmax activation function

You would only use linear activation function if you had a regression problem that goes into the negative numbers.

For the hidden layers, you can use ReLU, research has found that it is faster.

### Why we need activation functions

- What happens if we only use linear activation functions?
  - The output of the last layer is a linear function of the inputs
  - A linear function of linear functions is still a linear function
  - The whole network is equivalent to a single layer

![](./Screenshot%202023-06-06%20182218.png)

In linear algebra, a linear function of a linear function is still a linear function.

## Multiclass classification

- In binary we only need logistic regression, as we needed one curve to separate the two classes.
- In multiclass, we need to separate the classes, so we need multiple curves. Softmax is used to do this.

### Softmax

We use the softmax to calculate the probability of each class, much like in logistic regression, we use e^z to calculate the probability of the class.

![](./Screenshot%202023-06-06%20183303.png)

### cost function

The cost is just that -log(y_hat) that we had for logistic regression, now we just have to find the correct class, and say that the cost is how far away it was from predicting the correct class.

![](./Screenshot%202023-06-06%20183710.png)

### How to use softmax in a Neural Network

We keep the Neural Network the same, but we change the activation function of the last layer to softmax. That way we still get the possibility of each features, such as a face etc, but in the end gives you the probability of each class.

In tensorflow the only thing we need to change is the activation function of the last layer to softmax.

### Tensorflow specifics

Even though it would be easy to just change the last layers activation function to softmax, this creates a lot of numerical errors because e^x is a very large number or a very small number. So we use a trick to make it more stable.

Instead of getting the probability of each class being true, we get an output of z1 though zn and then we pass the output through the softmax function to get the probability of each class.

### Multilabel classification (multiple classes can be true)

The last node in a mutlilabel classification problem is sigmoid, because we want to know the probability of each class being true, they can for instance all be true. an output of a=[1 1 1]

## Optimizers

### Adam optimizer

The adam optimizer changes the learning rate of each parameter, so that it can learn faster. So if a learning rate is too high, the feature bounces back and forth, the learning rate is lowered. If the feature goes really slowly in the same direction, the learning rate is increased.

### Convolutional layers

In a convolutional layer, each node doesn't look at all the inputs in _a_ (the previous layer), but only a small part of it. This is called a receptive field. It allows it to work much faster, and also not overfit the data. Also forces the network to consider a part if we know its important. Like maybe you want to know what type of show it is, so you look at the bottom right because thats where the symbol is.

### Back prpagation Computational Graph

Its just derivative chainrule, but we calculate from right to left, because multiple nodes on the left can depend on the same node on the right.

![](./Screenshot%202023-06-07%20125854.png)
