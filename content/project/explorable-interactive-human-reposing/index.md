---
title: Explorable Interactive Human Reposing
date: 2021-12-09T03:53:18.992Z
summary: >-
  Human-AI Interaction Course project 2021 


  We design a notebook to allow the user to upload an image of a person and modify the pose of that person by dragging and dropping body joints.


  We use [CoCosNet-v2](https://github.com/microsoft/CoCosNet-v2) to synthesize the image of the reposed person. We use [OpenPose](https://github.com/Hzzone/pytorch-openpose) to extract the pose of the person. We use [ IPython widgets](https://ipywidgets.readthedocs.io/en/latest/) to enable interaction with the extracted pose.
draft: false
featured: false
authors:
  - Anirban Mukhopadhyay
  - Badour AlBahar
  - Hongjie Chen
tags:
  - Human reposing
  - Human-AI Interaction
links:
  - url: https://drive.google.com/file/d/1NzMc1fPWqjustazzCcdM9bBTBqwnsRS7/view?usp=sharing
    name: Jupyter notebook with interactive elements for human reposing
    icon_pack: fab
    icon: github
image:
  filename: featured.png
  focal_point: Smart
  preview_only: false
  caption: Interactive reposing
---


Design

* We first allow the user to read an image and we display the uploaded image to the user. 
* We then extract the pose from the body joint detection algorithm (OpenPose (https://github.com/Hzzone/pytorch-openpose)) and get two arrays (subset and candidate) representing the pose.
* We map these ambiguous arrays (subset and candidate) into a user understandable body joint skeleton and display them.
* We make the joints interactable, where users can drag and drop joints.
* We allow the user to click "replot" to get the final pose they want.
* We map the edited pose back into the ambiguous arrays (subset and candidate) to be passed into the reposing model (CoCosNet-v2 (https://github.com/microsoft/CoCosNet-v2)) to synthesize the final reposed image.
* We allow the user to use an image whose pose they like for pose extraction.
* We add "evaluate" button that will evaluate the accuracy of respecting the desired pose by utilizing the following metrics:

  * Average keypoint distance (AKD): the average distance between the pose keypoint of the output image and the input pose keypoint.
  * Missing keypoint rate (MKR): the number of pose keypoints not detected in the generated image.