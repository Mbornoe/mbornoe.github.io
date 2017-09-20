---
title:  "How to train SSD (Keras port) on your own data!"
date:   2017-09-20 15:04:23
categories: [Computer Vision, Deep Learning, Object Detection, Tutorial]
tags: [Computer Vision, Deep Learning, Object Detection, Tutorial]
---
I wanted to try out SSD for quite some time, I might even think this is timely overdue, but when wanting to find some tutorial on how to get things up and running on your own data, I did not really find any thorough guide that could speed up my learning curve significantly. So I decided to make my notes available here through a "small" guide.

In this guide I will walk you through how I trained the Single-Shot-Detector, **SSD**, on one of my own datasets. The port of SSD that I am using is the SSD_Keras port found at https://github.com/rykov8/ssd_keras. I am using the code in the dl-docker image, which can be found here https://github.com/floydhub/dl-docker, which I generally can recommend as I find it super easy to work with.

You might have figured out some parts of how you train your SSD network, or just want to take a look at my funny spelling errors in a specific section. Either way, for your convenience, here is a quick navigator overview of this guide's walkthrough parts/sections.

[TOC]

## What is SSD and how does it work?
-------------

## Lets get started / Requirements
-------------

## Convert annotations to SSD syntax
-------------
To get a really good idea of how the format works, I would recommend reading through issue [#15](https://github.com/rykov8/ssd_keras/issues/15) and [#19](https://github.com/rykov8/ssd_keras/issues/19) from [rykov8's ssd_keras Github repo](https://github.com/rykov8/ssd_keras).
Additionally, I would recommend taking a closer look into some of the code at the repo, particularly [get_data_from_XML.py](https://github.com/rykov8/ssd_keras/blob/master/PASCAL_VOC/get_data_from_XML.py) and [SSD_training.ipynb](https://github.com/rykov8/ssd_keras/blob/master/SSD_training.ipynb) which we eventually use later on for the entire setup and training.

### Syntax
-------------
The annotation format of the Keras port of SSD follows the below syntax:
> [xmin, ymin, xmax, ymax, prob_class1, prob_class2, prob_class3, ... , prob_class#NUM_CLASSES]

It is important to note that the xmin, ymin, x,max, and ymax are all in relative coordinates to its corresponding image, meaning that you need to divide all the x-coordinates and y-coordinates with the annotation's corresponding training image's width and height, respectively.
The *prob_class* corresponds to the "probability" of the specific annotation belonging to class 1, 2, 3, ..., up to the total number of classes in your training data, where the background is excluded for the ground truths (We will train the network with NUM_CLASSES+1).  So you just have to put a 1 in the specific prob_class where the annotation belong to. 

### Example
-------------
Let say we have some training data, where we have 6 classes (NUM_CLASSES = 6), and we have some training images with the size (width, height) = (640, 480), that we want to convert into the SSD syntax:
We define the 6 classes in this case to be:
> **Classes**
> "Van": "1", 
> "Car": "2", 
> "Pedestrian": "3", 
> "Lorry": "4",
> "Bus": "5", 
> "Cyclist": "6"

 We the have some "original annotations" that we have annotated in some traditional bounding box annotator program, which provides us with the following annotations:
> **[xmin, ymin, xmax, ymax, class]**
> [394, 167, 406, 178, 1]
> [374, 155, 394, 171, 5]
> [116, 336, 220, 425, 2]
> 

If we convert these into the SSD syntax we get the following:
> **[xmin, ymin, xmax, ymax, prob_class1, prob_class2, prob_class3, prob_class4, prob_class5, prob_class6]**
> [0.615625, 0.347916667, 0.634375, 0.370833333, 1, 0, 0, 0, 0, 0]
> [0.584375, 0.322916667, 0.615625, 0.35625, 0, 0, 0, 0, 1, 0]
> [0.18125, 0.7, 0.34375, 0.885416667, 0, 1, 0, 0, 0, 0]

### Put the annotations in a python dictionary
-------------
In the [SSD_training.ipynb](https://github.com/rykov8/ssd_keras/blob/master/SSD_training.ipynb) the annotation original code imports the annotation using pickle and put them into a python dictionary, where each key is the frame name with file extension in it. E.g. I can write I can print out the annotation from frame00104.png:
> gt = pickle.load(open('gt_pascal.pkl', 'rb'))
> print(gt['frame00104.png'])
> >[[ 0.840625    0.26388889  0.959375    0.64722222  0.          0.          1.        ]
 [ 0.31796875  0.78888889  0.50703125  0.99444444  0.          0.          1.        ]]

As the above code show, we can print out the converted annotation from the original example from the github repo, where you can see there is only 3 classes.

