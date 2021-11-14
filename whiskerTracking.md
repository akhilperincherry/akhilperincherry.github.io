## Aim and motivation

The goal of this work was to track rat whisker states using visual data. Rats use their whiskers to explore their environments in the context of object localization. In order to understand how whiser based tactile information is represented in the neural system, sensory input on the whiskers need to be quantified and correlated with the neural recordings during the whisking. Whisker tracking addresses the former problem.

## Setup

The rats were observed in a gap-crossing task consisting of two platforms, an IR illuminator and overhead camera. The gap in the box for the rat to cross is variable and can be adjusted. All whiskers of the rat except one was trimmed and head fixed rats were used for experimentation. The setup of the platforms and the camera is similar to the image below which was taken from [this](https://pubmed.ncbi.nlm.nih.gov/18463190/) paper. Aligning the platform edges to the side of the images in the camera setup reduces the difficulty of the problem resulting in simple image processing solutions.
<img src="images/GC_setup.PNG?raw=true"/>

## Solution

* The rat was detected using background subtraction and spatial filtering. 

* To find the orientation of the rat's head, pose estimation was performed to detect three keypoints corresponding to the two eyes and a nose. [Flowing ConvNets](https://arxiv.org/abs/1506.02897) was used for this.

* To perform whisker detection, [ConvNet toolbox](https://github.com/sdemyanov/ConvNet) was used.

* The whisker regressed outputs were fit using splines and tracking via Kalman Filter.

<img src="images/Whisker_1.PNG?raw=true"/>