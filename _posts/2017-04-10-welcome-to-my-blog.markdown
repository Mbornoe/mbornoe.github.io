---
title:  "Welcome to my blog"
date:   2017-04-10 15:04:23
categories: [General]
tags: [General]
---
My name is Morten Bornø Jensen and I am a PhD student at Aalborg University, Denmark, where I am also born and raised.  I have received by Master's Degree in Computer vision from Aalborg University in 2015. Directly after graduation I began working in the "Visual Analysis of People Laboratory" (VAP) at Aalborg University who is led by Professor Thomas B. Moeslund, who was also supervising my master's thesis. We are a very diverse and socially well functioning group of people in the VAP Lab, but are working on a lot of different things spanning from slaughterhouse robots to measuring activity level in sport arenas using computer vision. As you can see, the VAP lab specializes in a vary broad area, all within the are of computer vision, which also involve traffic surveillance - which is it area I will be doing my PhD thesis in.

## Thesis abstract
My thesis is about analyzing vulnerable road users(VRU) in the traffic scene using computer vision methods. The number of personal vehicles in Denmark has raised to 2.391.000 from 2015-2016 ([^fn1]) which correlated with 9 out of 10 danes owning a bike ([^fn2]) unfortunately presents a risk for accidents.


Traffic researchers have a desire to prevent these accidents and conflicts by capturing traffic data at e.g. selected intersections. The occurrence of near-accidents or conflicts are a lot higher than actual accidents ([^fn3]). A large amount of data is therefore needed in order to capture sufficient conflicts and accidents at a given site to make a statistically acceptable case. This can easily add up to hundreds of hours of traffic data, which is a very time consuming process for the traffic researchers to examine manually.


Computer vision is an obvious tool to automate parts of this very time consuming process. It can be used to detect and classify various objects in the traffic scene, e.g. vehicles, cyclists, or pedestrians. In order to replace a large part of the task, that is currently being done manually by the traffic researchers, a computer vision tool must be developed which ideally is able to detect and classify in all sorts of weather and lighting condition. This is however not a trivial task, thus making the tool fully automatic and able to replace traffic researchers completely is unrealistic within this thesis. Instead the tool should be considered a supporting tool for the traffic researcher for doing data reduction in in a "human-in-the-loop" manor. The tool must therefore be able to detect a variety of parameters as interesting traffic studies, e.g. conflict studies, is usually a combination of events such as multiple objects crossing paths or red running.


In order to meet the criteria of doing data reduction in varied traffic data captured continuously throughout several weeks, different capturing modalities are used. The most common image acquisition modality is RGB which is a good descriptor of a vehicle, cyclist, or pedestrian, but relies on proper lighting conditions which cannot be controlled outdoors. Therefore, two RGB streams from different angles at given intersection will be used and will be complemented with one thermal stream. The heat image from the thermal stream complements the RGB streams well during the night and furthermore sidesteps some of the privacy concerns that show up in systems like these.
In short, this thesis will study the usage of computer vision to do data reduction on traffic data with focus on vulnerable road users using RGB and thermal traffic scene data.

[^fn1]: Danmarks Statistik. Danskerne får flere og yngre biler. URL: http : / / www . dst . dk / da / Statistik/NytHtml?cid=26472 (visited on 06/14/2016).
[^fn2]: trafiktypen.dk. Cykel. URL: http://www.trafiktypen.dk/cykel (visited on 06/15/2016).
[^fn3]: C. Hydén. The Development of a Method for Traffic Safety Evaluation: The Swedish Traffic Conflicts Technique. Bulletin (University of Lund, Lund institute of technology, Department of traffic planning and engeneering). Ch. Hydén, 1987. URL: https://books.google.dk/ books?id=XGRfNAAACAAJ.

## Scientific content of my thesis
The thesis is about generating an semi-automatic analysis of the vulnerable road users in the traffic scene. The thesis can be broken down into five stages:


1. Large scaled multi-modal and multi-view data collection in traffic intersections.
2. Big data annotation using semi-supervised classifier.
3. Vulnerable road users(VRU) classification in the traffic scene using deep learning using multi- modal and multi-view data.
4. Semi-automatic VRU traffic analysis.
5. Using UAVs to generate traffic usage reports in roundabouts and intersections.


The first stage addresses capturing data with multiple cameras and modalities in traffic intersections. In this stage, equipment must be analysed with the scope of creating a robust capturing platform that can be deployed at intersections and capture data using batteries. A battery-powered recording platform has already been developed in cooperation with the Traffic Research Group at Aalborg University, but needs to be developed further such multiple cameras can be included.
The second stage deals with a major research issue of how to annotate large amount of data in a proper manor. By creating a reinforcement learning framework, one can manually annotate a small part of the dataset, and use this to create an object classifier which are applied yet another small part of the dataset. This workflow are iterated until the entire dataset are annotated, hence semi-automatic annotations using reinforcement learning with a feedback loop.
The third stage will include developing a robust vulnerable road users classification (VRU) framework. The classification module will be based on deep learning methods and the framework must be contain a graphical user interface such traffic researchers can use of it.
The fourth stage deals with developing of a semi-automatic VRU traffic analysis framework for traffic researchers. They will use it for data reduction on their large datasets, the framework must be able to adapt to changing environments by determining and adjusting parameters automatically.
The fifth and final stage will be to use a UAV (Unmanned aerial vehicle), i.e. a drone, to capture data at roundabouts or intersections in both the RGB and thermal domain. This data should be used as input to an automatic analysis tool, which can generate traffic reports based on the data, e.g. queue length on each roundabout leg, traffic density, entrance, and exit in the traffic scene, etc.

## Objectives of the thesis
To investigate methods using multi-view RGB and thermal data, as well as data capturing from UAV and 360◦cameras to classify traffic scene objects, such as cars, trucks, cyclists, and pedestrians. The final goal is to implement the investigated state-of-the-art methods into vulnerable road users classification (VRU) framework, such the latest computer vision state-of-the-art methods are made available for traffic researchers. The foundation of this work will rely on comprehensive data collection and experiments with different modalities and view angles.
The concrete research questions are:


- How can large amount of data be annotated in a semi-supervised manner?
- How can classification of traffic scene objects be improved using multi-modal and multi-view data to classify?
- How do object classification on UAV data perform compared to single-view and multi-modal and multi-view data?

## PhD Plans
Should anyone have an interest in reading my entire PhD plans, they made available here:

[2 Months PhD Plan](/files/phd-plans/2monthPhdPlan.pdf)

[11 Months PhD Plan](/files/phd-plans/11monthPhdPlan.pdf)

## Bibliography