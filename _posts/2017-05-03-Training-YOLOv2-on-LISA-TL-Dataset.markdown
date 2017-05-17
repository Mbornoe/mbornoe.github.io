---
title:  "'You-only-Look-Once'(YOLO) at the LISA Traffic Light Dataset"
date:   2017-05-03 15:04:23
categories: [Computer Vision, Deep Learning, Traffic Light Detection, Tutorials]
tags: [Computer Vision, Deep Learning, Traffic Light Detection, Tutorials]
---
As clearly visible in my publications found in the [research](http://mbornoe.github.io/research.html) page, I am quite active in research related to traffic light detection, which is a "Driving Assistance System" and ultimately an autonmous driving application. One of the biggest current *buzzwords* is AI, short for **Artificial Intelligence**, which might be best known due to some sci-fi movies. AI is however so much more and so much different, than killer robots and other sinister doomsday threats. AI consists of so many applications, that you can easily get confused on how to actually define it. To me, research in AI is to make a machine able to perceivve some environment or case and based on that maximize some output, which in my case could be the probability of detecting traffic lights. What is quite interesting about AI applied in computer vision is the way we try to make a machine *mimic* the cognitive functions seen in humas, such as (self)learning and problem solving. In my field of research, this is usually refered to as **deep Learning**, which often is related to neural networks. My latest publication, "Evaluating State-of-the-art Object Detector on Challenging Traffic Light Data", has just been accepted at the CVPR workshop, "Traffic Surveillance Workshop and Challenge". In this paper, I have applied the 'You-only-Look-Once' (YOLO) framework at the [LISA Traffic Light dataset](http://cvrr.ucsd.edu/vivachallenge/index.php/traffic-light/traffic-light-detection/). If you you do not really have any interest in the specific methods, you should just skip directly to the button, where I have made a video available of the best performing method applied on the daySequence1 from the [LISA Traffic Light dataset](http://cvrr.ucsd.edu/vivachallenge/index.php/traffic-light/traffic-light-detection/).

## 'You-only-Look-Once' (YOLO)
YOLO is an end-to-end single convolutional neural network that detects objects based on bounding boxes prediction and class probabilities. The network divides the input image into a SxS grid, if the center of an object is located within this grid, it is this specific grid's task to detect the object. Each grid predicts bounding boxes and a corresponding confidence, where the confidence is an indicator of how confident the model is that a box contains an object as well as how accurate the box is. The confidence is therefore calculated using the intersection over union (IOU), where a perfect match between a predicted box and a ground truth will provide a confidence of 1, and oppositely if a predicted box is not present in the grid, hence no ground truth overlapping, the confidence will be 0. Finally, the grid cell also predicts the probability of an object belonging to a class. 

## Results
I trained a quite a few different model, which can be seen in below figure:

![consortium](/images/posts/yolo_cvpr_tld/tldTable.png)

The training data is mainly from the [LISA Traffic Light dataset](http://cvrr.ucsd.edu/vivachallenge/index.php/traffic-light/traffic-light-detection/), but the French 
[LARA Traffic Light database](http://cvrr.ucsd.edu/vivachallenge/index.php/traffic-light/traffic-light-detection/) is also included in some of the configurations. The *random* parameter enables multi-scale training, resulting in a robustness for detecting objects in different image resolutions. The input size is per default set to a resolution of (416x416), but by enabling the random parameter the network will randomly change the input image size every 10 batch. The YOLOv2 network downsamples by a factor of 32, resulting in a downsampling range between \{320, 352, ..., 608\}. The smallest input size is thus (320x320), and the largest input size is (608x608). The random parameter is per default enabled in YOLOv2, in this paper we will try to identify the effect. Each of the 6 models from the above table is trained for up to 80,000 iterations, where the model usually converges around 35-40,000 iterations.  For further procesing, the iteration with the highest recall from each of the 6 models is to plot a Precision-Recall(PR) curve. The recall iterations plots can be seen in below figure for models with model's input image is 416x416 in first plot and resized to 672x672 in the second plot.

![consortium](/images/posts/yolo_cvpr_tld/recall416.png)

![consortium](/images/posts/yolo_cvpr_tld/recall672.png)

 From this PR-curve the "Area-Under-Curve" is measured and used as the final metric. Below are two figures shown where the model's input image is 416 in first plot and resized to 672 in the second plot.

![consortium](/images/posts/yolo_cvpr_tld/PRC-AUC-416.png)

![consortium](/images/posts/yolo_cvpr_tld/PRC-AUC-672.png)

## Video
Below is a video shown of the DaySequence1 from the [LISA Traffic Light dataset](http://cvrr.ucsd.edu/vivachallenge/index.php/traffic-light/traffic-light-detection/), where the model YOLO_V3_1 is used, which was the best performing with an AUC of 90.49 %.
[![Everything Is AWESOME](https://mbornoe.github.io/images/post/yolo_cvpr_tld/yoloVideoYoutube.png)](https://youtu.be/XtPoE1NuXfA "Everything Is AWESOME")