---
layout: post
title: "Deep Learning Concept 3: Learning Rate"
---

### What is a learning rate?
Learning rate is a hyper-parameter that controls how much we are adjusting the weights of our network with respect to the loss gradient

$$new_weight = existing_weight - learning_rate * gradient$$

### Why is learning rate important?
Learning rate affects how quickly our model can converge to a local minima. Choosing a bad learning rate can results in network either fail to train or take much longer to converge.

### How to choose the best learning rate?
First we need to find the optimal learning rate range. The idea is that when learning rate is too low, the loss may also decrease very slow. When it gets into optimal range, the loss will drop quickly and when it gets out of optimal range, the loss will bounce around and even diverge from minima. In this way, we can know what is the optimal range.
Then after that, during training there are two way we can automatically adjust the learning rate:
1. learning rate annealing: start with relatively high learning rate and then gradually lowering the learning rate during training. The idea is that we can quickly get to the area of local minima and then find the local minima through small learning rate
2. Cycle learning rate: initially proposed in this [paper](https://arxiv.org/abs/1506.01186). The author proposed a cyclical learning rate schdule which bounced between two values. It is a triangular update with either fixed cyclic decay or an exponential cyclic decay.

