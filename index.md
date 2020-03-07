---
layout: default
---

# Abstract
**Pose-guided person image generation** is to transform a source person image to a target pose. This task requires spatial manipulations of source data. However, Convolutional Neural Networks are limited by lacking the ability to spatially transform the inputs. In this paper, we propose a differentiable **global-flow local-attention framework** to reassemble the inputs at the feature level. Specifically, our model first calculates the global correlations between sources and targets to predict flow fields. Then, the flowed local patch pairs are extracted from the feature maps to calculate the local attention coefficients. Finally, we warp the source features using a content-aware sampling method with the obtained local attention coefficients. The results of both subjective and objective experiments demonstrate the superiority of our model. Besides, additional results in video animation and view synthesis show that our model is applicable to other tasks requiring spatial transformation.


# Network Architecture
Our network spatially transforms the image features using a **Global-Flow Local-Attention** framework. First, the Flow Field Estimator is used to obtain the global flow fields which indicate the approximate sampling positions.
![Octocat](https://user-images.githubusercontent.com/30292465/75703936-66385e80-5cf3-11ea-9743-c0cce2fe6458.jpg)

Then, the local attention operation is performed for each local patch in the target features centered at position _l_. This operation allows the network sampling vivid textures from the source features according to the target pose. 
![Octocat](https://user-images.githubusercontent.com/30292465/75703859-42751880-5cf3-11ea-985b-8ed27ba5433b.jpg)

# Results and Applications

## Pose-based Person Image Generation
<p align='center'>  
  <img src='./compare.pdf' width='600'/>
</p>
<p align="center">
  Form Left to Right: Source, Target Pose, Target Image, <a herf="https://arxiv.org/abs/1801.00055">DefGAN</a>, <a herf="https://arxiv.org/abs/1804.04694">VU-Net</a>, <a href="https://arxiv.org/abs/1904.03349">Pose-Attn</a>, <a href="http://mmlab.ie.cuhk.edu.hk/projects/pose-transfer/">Intr-Flow</a>, Ours.
</p> 

## Image Animations

* **DeepFashion:**
In this task, we use a source image and a sequence of target poses to generate the result video. This task can be seen as an extension of pose-based person image generation, which yields continuous videos.


<p align='center'>  
  <img src='https://user-images.githubusercontent.com/30292465/75778006-fe852080-5d91-11ea-8e76-dd87f6c021f7.gif'/>
</p>

<p align="center">
<b>From Left to Right</b>: Real Video, Extracted Pose, Animation Results.
</p>

* **Face Animation:**
Given a source face and a sequence of edge images, our model generates the result video with specific motions.

<p align='center'>  
  <img src='https://user-images.githubusercontent.com/30292465/75703614-c1b61c80-5cf2-11ea-8730-52eaeaea08e7.gif' width='760'/>
</p>

<p align="center">
    <b> Left</b>: Input Source Image and Edge Sequence, Right: Animation results.
</p>

## View Synthesis

* **ShapeNet:**
View synthesis requires generating novel views of objects or scenes based on arbitrary input views. In this task, we generate multi-images with different view points based on a single input source image.

<p align='center'>  
  <img src='https://user-images.githubusercontent.com/30292465/75703558-a9460200-5cf2-11ea-86a1-e5a651d8f727.gif' width='760'/>
</p>

<p align="center">
Form Left to Right: Source, Results of <a href="https://arxiv.org/abs/1605.03557">Appearance flow</a>, Ours, and Ground-truth images.
</p> 