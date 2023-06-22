## Recommender System

### Notation

n_u: number of users
n_m: number of movies
r(i,j): 1 if user j has rated movie i, 0 otherwise
y(i,j): rating given by user j to movie i (defined only if r(i,j)=1)
x(i): feature vector of movie i
m(j): how many movies user j has rated

The weights and biases are different for each user, so we index them with.
Each user has a different linear regression model to predict the ratings.

![](./Screenshot%202023-06-18%20185238.png)

### Cost Function

**For a single user**
The cost function for recommender systems is essentially the same with one main differences, we only have a truth value y, for movies the user has actually rated. So we sum for all i as long as r(i,j)=1 and we divide by the number of movies the specific user has rated. Similarly the normalization term is also different, we sum over all features but we divide by the number of movies the user has rated.

**Note**: you can also completely get rid of the m(j) term since it is a constant and it will not affect the minimization of the cost function.

![](./Screenshot%202023-06-18%20185754.png)

**For all users**
The cost function for all users is the sum of the cost function for each user. The regularization term is the same as before.

## What happens if you don't have features?

This can happen if you don't have time to label each video by how funny or action-filled it is. In this case, you can use the collaborative filtering algorithm. This algorithm will learn the features on its own.

It is now learning and updating the features each step of gradient descent. We now have a new cost function.
**NOTE**: We are regularizing the x terms.

![](./Screenshot%202023-06-20%20200540.png)

## Collaborative Filtering Algorithm

Combines both the user-based and item-based approaches. It is a way of automatically learning both the user preferences and item features at the same time.

![](./Screenshot%202023-06-20%20222343.png)

Update the x and theta terms simultaneously.

![](./Screenshot%202023-06-20%20222443.png)

### Notation summary

![](./Screenshot%202023-06-21%20145738.png)
