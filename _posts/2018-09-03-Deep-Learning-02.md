---
layout: post
title: "Deep Learning Concept 2: mAP on object detection"
---

Object detection model evaluation has two parts: what object it is (classification) and where it is (localization).

To evaluate the classification part, there are two useful metrics: precision and recall. They are defined as 

$$Precision = \frac{true_positive}{true_positive + false_positive}$$

$$Recall = \frac{true_positive}{true_positive + false_negative}$$

Precision says how many correct objects are detected out of all detected objects. Recall says how many correct objects are detected out of all labelled objects. There is a inverse relationship between precision and recall. The higher precision is, the lower recall is and vice versa. To compare two classification algorithm, you can directly compare the two curves. However we have one problem here: most curves are zigzagged, meaning the two curve you compare will intersects a lot. Therefore, an reasonable way to compare these curve is to calcualte the area under curve (AUC). We define AP as

$$AP = \sum_{n} (R_{n} - R_{n-1})P_{n}$$

where $$P_{n}$$ and $$R_{n}$$ are the precision and recall at the nth threshold.

Up till now, we are only evaluating classification result. To evaluate localization, we need to calculate intersection over union (IoU). We define a correct object detection as one with IoU larger than a threshold. Then mAP is defined as average AP among all IOU threshold. mAP@.75 means the mAP with IoU-0.75