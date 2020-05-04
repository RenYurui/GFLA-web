---
layout: simple
---

<p align='center'>  
  <img src='./head.pdf' width='900'/>
</p>

# **Abstract**
**Pose-guided person image generation** is to transform a source person image to a target pose. This task requires spatial manipulations of source data. However, Convolutional Neural Networks are limited by lacking the ability to spatially transform the inputs. In this paper, we propose a differentiable **global-flow local-attention framework** to reassemble the inputs at the feature level. Specifically, our model first calculates the global correlations between sources and targets to predict flow fields. Then, the flowed local patch pairs are extracted from the feature maps to calculate the local attention coefficients. Finally, we warp the source features using a content-aware sampling method with the obtained local attention coefficients. The results of both subjective and objective experiments demonstrate the superiority of our model. Besides, additional results in video animation and view synthesis show that our model is applicable to other tasks requiring spatial transformation.


# **Network Architecture**
The **Global-Flow Local-Attention** model is used to spatially transform the source image information at the feature level. A Global Flow Field Estimator is first employed to predict the flow fields between sources and targets. Then, a Local Neural Texture Renderer is used to to synthesize the final results using local attention.
![Octocat](./2e0fc90ebb6d82d09c482744c228ba90.jpg)

The local attention blocks in the Local Neural Texture Renderer are responsible for transforming source information. The transformation process is shown below. For each target position, the corresponding local patch pair is first extracted. Then the local attention coefficients are predicted for content-aware sampling.
![Octocat](https://user-images.githubusercontent.com/30292465/75703859-42751880-5cf3-11ea-985b-8ed27ba5433b.jpg)

# **Results**
### **Pose-Guided Person Image Generation**
<p align='center'>  
  <img src='./compare.pdf' width='800'/>
</p>
<p align="center">
  Form Left to Right: Source, Target Pose, Target Image, <a herf="https://arxiv.org/abs/1801.00055">DefGAN</a>, <a herf="https://arxiv.org/abs/1804.04694">VU-Net</a>, <a href="https://arxiv.org/abs/1904.03349">Pose-Attn</a>, <a href="http://mmlab.ie.cuhk.edu.hk/projects/pose-transfer/">Intr-Flow</a>, Ours.
</p> 

### **Pose-Guided Person Image Animation**



<p align='center'>  
  <img src='https://user-images.githubusercontent.com/30292465/75778006-fe852080-5d91-11ea-8e76-dd87f6c021f7.gif'/>
</p>

<p align="center">
<b>From Left to Right</b>: Real Video, Extracted Pose, Animation Results.
</p>

### **Face Image Animation**
Given a source face and a sequence of edge images, our model generates the result video with specific motions.

<p align='center'>  
  <img src='https://user-images.githubusercontent.com/30292465/75703614-c1b61c80-5cf2-11ea-8730-52eaeaea08e7.gif' width='760'/>
</p>

<p align="center">
    <b> Left</b>: Input Source Image and Edge Sequence, Right: Animation results.
</p>


### **Novel View Synthesis**
View synthesis requires generating novel views of objects or scenes based on arbitrary input views. In this task, we generate multi-images with different view points based on a single input source image.

<p align='center'>  
  <img src='https://user-images.githubusercontent.com/30292465/75703558-a9460200-5cf2-11ea-86a1-e5a651d8f727.gif' width='760'/>
</p>

<p align="center">
Form Left to Right: Source, Results of <a href="https://arxiv.org/abs/1605.03557">Appearance flow</a>, Ours, and Ground-truth images.
</p> 