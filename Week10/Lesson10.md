## Reinforcement Learning

Reinforcement learning is an algorithm in which we only give a specific reward function, ie. tell the robot what is good and what is bad, and let the robot learn by itself. The robot will try to maximize the reward function.

At each point in the process, the robot has a state, and it will take an action. The action will change the state of the robot, and the robot will get a reward. The robot will try to maximize the reward function.

![](./Screenshot%202023-06-23%20182905.png)

### Discount factor

This is a way to disensentivize slowness, and to encourage the robot to finish the task as soon as possible. The discount factor is a number between 0 and 1. The reward function is multiplied by the discount factor to the power of the number of steps it takes to finish the task. The discount factor is usually 0.9.

**The discount factor will force positive rewards to be closer to the present, and negative rewards to be as far in the future.**

![](.//Screenshot%202023-06-23%20183043.png)

### Markov Decision Process

A Markov Decision Process is a way to model the problem.

Where the current state is a ground truth, the past doesn't affect you, and you are trying to perform an action to get to the next state, which should maximize the reward function in the long run, but not too far in the future, because of the discount factor.

### State value function

The state value function tells you your total reward from a given state after taking an action. It is the expected value of the reward function.

Notice how you can generate the optimal action in a policy with the max of the state value function at each state.

> _In this visualization I made the discount factor really low so that the robot will try to finish the task as soon as possible. It is willing to ditch the 100 reward for the closer 20._

![](./Screenshot%202023-06-24%20141134.png)

### Bellman equation

This Q is just the optimal policy so how is it possible to get it? Well you don't you simply recursively calculate it at each step using the Bellman equation.

![](Screenshot%202023-06-24%20142250.png)

### Stochastic environments

In a real world setting not all the electical components respond perfectly. So we can say that even though you try to take an action, maybe a slightly different action will be taken. This is called a stochastic environment.

Example: In the pupper robot, we added random forces on different parts of pupper so simulate it being knocked around. And we added a random offset to the force output by the motors to simulate the motors not being perfect.

This slightly changes the state value (Q) function, because we have to take the average of an action or the expected value of an action.

> _We have a large chance (90) of going to 2 which is the optimal action, but there is a small chance (10) of going to 4 which is less optimal but still gives us a reward. Note that the optimal action is still 2. If we changed the output to 4, we would have a 90% chance of going to 4, and a 10% of going to 2_ > ![](./Screenshot%202023-06-24%20142752.png)

**Adding stochasticity will make the robot choose the safer bet, not taking risky steps. This mirrors old humans who will use the handrail even though it slows them down because they might misstep and fall, the average of the possible rewards mutliple high, and one really low makes it so the safer action is preffered.**

## Deep Reinforcement Learning

### Goal

We are trying to train a deep neural network with inputs of the current state, to predict the optimal action to take. Ie. we are trying to train a neural network to predict the Q function.

What we just described is supervised learning, but we don't have the labels, ie. we don't know what is the optimal action to take or even what reward we will get if we take an action.

### Making a dataset

You take a series of completely random actions, and record the state, action, reward, and next state. You can then create a dataset thus:

> _X is your current state and action you took [Q(s, a)]. Y is the reward you got plus feeding your next state and random action you took through your random State Value function._ > ![](./Screenshot%202023-06-24%20150526.png)

### Training

Now with a dataset consisting of random motions, you can train your neural network to predict the Q function. You will then make a new dataset with the new Q function, and train again. You will repeat this process until the Q function converges.

### Network architecture

The network takes in the current state and outputs the Q function for each action. The action with the highest Q function is the optimal action.

This is efficient because all the actions are being computed simultaneously. And it is really easy to pick the optimal action.

![](./Screenshot%202023-06-24%20151624.png)

### Epsilon greedy dataset

While at a current state, we already have a guess as to what the optimal action is, but we want to explore other actions to see if they are better. So we will take a random action with a probability of epsilon, and take the optimal action with a probability of 1 - epsilon.

This is called Exploration vs Exploitation. Where exploration is taking random actions to see if they are better, and exploitation is taking the optimal action.

**Epsilon technique:** You start with a really high epsilon, a lot of random exploration, and then slowly decrease it as the Q function converges. This is because you want to explore a lot at the beginning, but as you get closer to the optimal Q function, you want to exploit more.

### Notes

- RL is very finicky with hyperparameters, and it is hard to know what to set them to. You can use a grid search to find the best hyperparameters.

## Optimizations

### Mini-batch

Randomly sample a small batch of data from the dataset, and train on that. This is more efficient than training on the entire dataset.

While minibatch learning will not always head to the local minimum, maybe the examples you chose were particularly bad, it will always head to a good minimum over time. And each step is much faster so it can do many more steps, resulting in a better minimum.

![](./Screenshot%202023-06-24%20165416.png)

### Soft update

This update method is used in tandem with mini-batch learning where you don't fully accept the new weightws of the NN Q function, but you slowly update the weights of the NN Q function to the new weights with a specific rate.

![](./Screenshot%202023-06-24%20165742.png)
