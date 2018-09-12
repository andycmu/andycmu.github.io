---
layout: post
title: "Deep Learning Concept 7: softmax"
---

### Why we need softmax?
In binary classification problem, we can use logistic regression to do the classification, namely compute the probability of each class. In multi-class classification, we need to have a similar way to convert the neural network output to the probability for each class. Softmax helps us with this.

### What is softmax?
Softmax is an activation function like sigmoid and relu. It applies non-linearity to the last layer and outputs a probability for each class. The sum of the output vector value from softmax layer will be 1. Simple python implementation:

```python
logits = [2.0, 1.0, 0.1]
import numpy as np
exps = [np.exp(i) for i in logits]
sum_of_exps = sum(exps)
softmax = [j/sum_of_exps for j in exps]
```

### How to train with softmax
Since softmax helps you convert the output to a vector of probability for each class, you can calculate the [*cross-entrop loss*](https://andycmu.github.io/Deep-Learning-06) using softmax output. Then to calculate the cost J of the entire training set, you average the loss of each training example. At last, we can calculate the gradient descent of cost J and back prop the value.