## Clustering

### K-Means Clustering

The way K-Means works, is to decide random points which are cluster "centers", and then assign each point to the closest cluster center. Then you move the cluster center to the average of all the points in the cluster. Then you repeat this process until the cluster centers stop moving.

Effectively, you are trying to minimize the distance between the cluster centers and the points in the cluster. Slowly putting the points into the cluster that is closest to them.

![](./Screenshot%202023-06-15%20235343.png)

### Cost (distortion) function

The cost function, is how far away the centroids are from the points in the cluster. You want to minimize this cost function.

![](./Screenshot%202023-06-16%20005451.png)

### Anomaly detection

Anomaly detection is a statistical algorithm that says if a specific data point is an anomaly in your data set or not.

What it does is get the gaussian distributions of each variable on its own, and then calculate the gaussian probablility of each variable. Then multiply them all together for the probability of your entire feature vector.

![](.//Screenshot%202023-06-15%20203910.png)

### How to Develop and test your anomaly detection

First you train your algorithm normally, on non-anomalous data.

You can then cross_validate and tweak the paramaters using the cross validation data.

Once you have done that you can use the test data to test accuracy.

**IMPORTANT**: Both the CV and the Test data should contain labeled anomalies, this way you can set your epsilon for a boundary probability and check if the algorithm actually works.

![](./Screenshot%202023-06-15%20204223.png)

### Anomaly detection vs. Supervised learning

Anomaly detection is an algorithm that clusters around the normal, and will flag anything that is new and hasn't seen the likes of before.

On the otherhand, supervised learning will find the same pattern on current anomalies and flag them in the future.

Summary:

- If you have very little anomalous cases, and there could be completely new unseen anomalous cases in the future such as in electrical outages causing strain on the grid (changes all the time) we should use **Anomaly detection**. It will flag anything that isn't normal. On the other hand Supervised learning would only flag the outages similar to the previous ones.

- If you have a lot of labeled anomalous cases, and you are quite confident new types of anomalies won't show up then Supervised learning (classification) is very useful. Such as in climbing rope testing, you know there aren't many ways it could break, and all the ways it could have already been found.

### Anomaly detection feature tuning

All the features going into your anomaly detection algorithm should be semi gaussian, otherwise a gaussian distribution won't categorize them properly. So you must engineer your features.
Here are some examples:

![](./Screenshot%202023-06-15%20211148.png)

Play around!

![](./Screenshot%202023-06-15%20211827.png)
