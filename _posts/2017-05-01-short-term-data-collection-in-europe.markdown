---
title:  "Short term data collection in Europe"
date:   2017-05-01 15:04:23
categories: [InDeV, Data Collection]
tags: [InDeV, Data Collection]
---
As part of my involvement in the [InDeV Project](http://www.indev-project.eu/InDeV/EN/Home/home_node.html) , where I am mainly aid technical assistance and guidance, a workpackage involved collecting data at multiple locations in Europe. To be more specific, InDeV have a desire to collect and compare data from intersections in 5 European countries. The purpose is twofold: testing the consistency of the safety indicators in between-site comparison, and testing and devel- oping reliable technical tools for automatic data reduction of the enormous traffic datasets captured with this project.

## Introduction
In total there will be collected data at 21 different intersections in Belgium, Denmark, Netherlands, Poland and Spain. The intersections are chosen based on previous traffic accidents involving vulnerable road users (VRUs) and their in-between site uniformity. The data collection at each site will be done in 3 consecutive weeks using a total of 3 cameras. In parallel with the data collection, a watchdog system is being develop which automatically detects near-accidents and accidents in the captured data.

## The system
At each of the 21 intersections, an identical setup will be installed for 3 weeks. Each setup consists of 2 capturing units with respectively 1 RGB and 1 Thermal camera, and 1 RGB camera. Most common datasets captured at intersections usually only deploy 1 RGB camera which usually cause a lot of occlusions and issues in varying lighting and weather conditions. Having 2 capturing units placed at carefully selected locations in an intersection provides the project with a multi-modal and viewpoint dataset. The two modalities, RGB and thermal, complements each other very well as thermal generates a "heat-image" making it ideal for night-vision where RGB cameras are challenged due to low to no light.
In order to make the data useful for further automatic analysis, the captured data must be time synchronized. This is done by creating a wireless network in the intersection connecting the two units together. Each unit has a server whereon all the data are stored. The server from the unit with 2 cameras is the master clock and is hosting a NTP server which the other unit with 1 camera synchronizes with. Finally the setup is powered by 3 large truck batteries providing 180 Ah @ 12V each. A simplified illustration of the entire setup is seen in below figures.

![simpleSetup](/images/posts/short-term-filming/setup.png)*Simple overview figure*







![techSetup](/images/posts/short-term-filming/WP4_1setup.png)*Technical overview figure*