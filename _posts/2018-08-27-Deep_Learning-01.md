---
layout: post
title: "Deep Learning Concept 1: non-maximum suppression"
---

### Problem it tries to solve
object detection algorithm may find multiple objects of the same objects. Non-maximum suppression makes sure that the algorithm only output one detection per objects.

### How it works
```
Discard all boxes with p < threshold (e.g. 0.6)
While (remaining box number > 0):
	pick the box b with largest p and output it as prediction
	remove all the boxes with IOU >= 0.5 with box b
```
