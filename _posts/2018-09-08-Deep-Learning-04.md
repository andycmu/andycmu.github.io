---
layout: post
title: "Deep Learning Concept 4: Mini Batch"
---

### What is mini batch
To understand what is mini batch, let's first take a look at **batch gradient descent**. For batch gradient descent, in each iteration you go through all the training data. You expect the cost to go down on **every single** iteration.

In **mini batch gradient descent**, each iteration has slower batch size and it takes many iteration to finish one epoch. For each iteration, you do forward prop on training data, compute cost using loss function, compute gradient descent of cost, back prop and update weights. Therefore, you are doing all the steps we do for batch gradient descent in each mini batch iteration.

Two extremes of mini batch:  
mini batch size = M (# of training examples): Batch gradient descent; will converge steadily but take too long per iteration.  
minibatch size = 1 is stochastic gradient descent; will not converge, will see cost change every single training example, but lose the speed up from vectorization.

### How do you choose mini batch size?
Small training set: e.g. less than 2000, use batch gradient descent.  
Large training set: possibly use mini-batch size range from 64 to 512. Make sure your minibatch fit in CPU/GPU memory 
