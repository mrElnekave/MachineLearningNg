### What is Supervised Learning?

It is just a learning technique where the right answers are given.

Example: Housing Price Prediction (Machine learning)

![img](./Screenshot%202023-05-21%20192049.png)

Learn to Map X inputs to Y outputs, with minimal cost.

### Types of problems

Regression Problem: Predict continuous valued output (price)

- Features (size, number of rooms, etc)
- Target variable (price)
- The model will predict given (x and gets ŷ)
- The f (hypothesis function) has a weight and a bias, where f = wx + b, f = w1x1 + w2x2 + b

Classification Problem: Discrete valued output (0 or 1) -> sigmoid function or boundary line

### Unsupervised Learning

Given a dataset without labels, you need to find some structure in the data, and group it.

Example: Google News

It finds all the categories alone.

![img](./Screenshot%202023-05-21%20193006.png)

Other uses: Anomaly detection (fraud detection), dimensionality reduction (find the most important variables)

### Cost function and how to use notation

We sum through all of our points, of which we have m, and then divide m times, as we want to find the average, and not have our error grow with number of datapoints.

![img](./Screenshot%202023-05-21%20200313.png)
