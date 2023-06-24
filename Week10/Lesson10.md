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
