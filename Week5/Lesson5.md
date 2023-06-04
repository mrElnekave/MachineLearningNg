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
