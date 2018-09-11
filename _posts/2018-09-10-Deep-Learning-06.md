---
layout: post
title: "Deep Learning Concept 6: cross entropy loss"
---

The most common loss function used in machine learning are MAE (mean absolute error), MSE (mean squared error) and cross entropy loss. This blog introduces cross entropy loss.  
We calcualte this loss for classification model which outputs a probability for each class.  

### Explanation with intuition
this loss increases when the probability of prediction diverges from ground truth, namely if the gt label is 1 while we predict 0.1 probability for label 1. Because we are calculating log, the loss increase rapidly when the probability is close to 0.  

### Explanation with math
**Calculation of probability happens only when the prediction matches with the ground truth**.  

For binary classification: $$-(ylog(p) + (1 - y)log(1 - p))$$  
where p is the probability for class 1.  

For multi-class classification: $$\sum_{c=1}^{M}y_{o,c}log(p_{o,c})$$  
where M is number of classes;  
y is the binary indicator (0 or 1) if class label c is the correct classification for observation o;  
p is the predicted probability observation o is of class c..

### Explanation with code
Code for binary classification:
```python
def CrossEntropy(yHat, y):
    if y == 1:
      return -log(yHat)
    else:
      return -log(1 - yHat)
```

Code for multi-class classification:
```python
def CrossEntropy(probability_list, ground_truth_label):
# probability_list is a list of probability that corresponds with each label
# ground_truth_label is an integer ranging from 0 to len(probability_list) - 1
    return -log(probability_list[ground_truth])
```