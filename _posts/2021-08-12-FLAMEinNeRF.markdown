---
layout: post
title: '<img  src="/images/FLAMEinNeRF/fire.png">FLAME-in-NeRF<img src="/images/FLAMEinNeRF/fire.png">: Neural control of Radiance Fields for Free View Face Animation'
author: ShahRukh Athar, Zhixin Shu Dimitris Samaras
---
<!--h1 align="left"><img height="20" width="16" src="/images/FLAMEinNeRF/fire.png">FLAME-in-NeRF<img height="20" width="16" src="/images/FLAMEinNeRF/fire.png">: Neural control of Radiance Fields for Free View Face Animation</h1-->
<head>
  <title>FLAME-in-NeRF: Neural control of Radiance Fields for Free View Face Animation</title>
</head>
<p>
<a href="http://shahrukhathar.github.io/about/" target="_blank">ShahRukh Athar</a>,
<a href="https://zhixinshu.github.io/" target="_blank">Zhixin Shu</a>, 
<a href="https://www3.cs.stonybrook.edu/~samaras/" target="_blank">Dimitris Samaras</a>
</p>
<br>
<br>
<div align="center">
  <a href="https://arxiv.org/abs/2108.04913">
    <figure style="display:inline-block;">
      <img height="100" width="78" src="/images/FLAMEinNeRF/paper-thumb.png">
      <figcaption>Paper</figcaption>
  </figure>
  </a>
  &nbsp;
  <a href="http://shahrukhathar.github.io/2021/08/12/FLAMEinNeRF.html">
    <figure style="display:inline-block;">
      <img height="100" width="100" src="/images/github.png">
      <figcaption>Code (On the way!)</figcaption>
    </figure>
  </a>
</div>
<br>
<br>
<div class="embed-container" style="position:relative;padding-bottom:41.56%;">
<video  style="width:100%;height:100%;position:absolute;left:0px;top:0px;" src="/videos/FLAMEinNeRF/Subj4_Drive.mp4" poster="/videos/FLAMEinNeRF/Subj4_thumb.png" controls>
  This is fallback content to display for user agents that do not support the video tag.
</video>
</div>
<p style="font-size:12px"><i><b>FLAME-in-NeRF:</b>  Our method enables expression-based reanimation of Portrait Neural Radiance Fields (NeRFs). On the right is the driving video from which expression parameters are drive the reanimated output of our method, which is shown on the left. As can be seen, the reanimated frames retain high fidelity to the target expression of the driving frame while, while simultaneously, respecting the individual characteristics of each subject.</i></p>

<br>
<div align="center">
  <br>
  <p style="font-size:17px"><i><b>TL;DR </b> FLAME-in-NeRF enables expression-based reanimation of portrait neural radiance fields.</i></p>
  <br>
  <br>
</div>

<br>
<div align="center">
<br>
<h1 style="text-align: center">Abstract</h1>
</div>

This paper presents a neural rendering method for controllable portrait video synthesis.
Recent advances in volumetric neural rendering, such as neural radiance fields (NeRF), has enabled the photorealistic novel view synthesis of static scenes with impressive results. However, modeling dynamic and controllable objects as part of a scene with such scene representations is still challenging. 
In this work, we design a system that enables both novel view synthesis for portrait video, including the human subject and the scene background, and explicit control of the facial expressions through a low-dimensional expression representation.
We leverage the expression space of a 3D morphable face model (3DMM) to represent the distribution of human facial expressions, and use it to condition the NeRF volumetric function.
Furthermore, we impose a spatial prior brought by 3DMM fitting to guide the network to learn disentangled control for  scene appearance and  facial actions.
We demonstrate the effectiveness of our method on free view synthesis of portrait videos with expression controls. To train a scene, our method only requires a short video of a subject captured by a mobile device.

<br>
<div align="center">
<br>
<h1 style="text-align: center">Some Results</h1>
</div>

Below we show reanimation results across different subjects.

<div class="embed-container" style="position:relative;padding-bottom:41.56%;">
<video  style="width:100%;height:100%;position:absolute;left:0px;top:0px;" src="/videos/FLAMEinNeRF/Subj1_Drive.mp4" poster="/videos/FLAMEinNeRF/Subj1_thumb.png" controls>
  This is fallback content to display for user agents that do not support the video tag.
</video>
</div>
<br>
<br>
<div class="embed-container" style="position:relative;padding-bottom:41.56%;">
<video  style="width:100%;height:100%;position:absolute;left:0px;top:0px;" src="/videos/FLAMEinNeRF/Subj2_Drive.mp4" poster="/videos/FLAMEinNeRF/Subj2_thumb.png" controls>
  This is fallback content to display for user agents that do not support the video tag.
</video>
</div>
<br>
<br>
<div class="embed-container" style="position:relative;padding-bottom:41.56%;">
<video  style="width:100%;height:100%;position:absolute;left:0px;top:0px;" src="/videos/FLAMEinNeRF/Subj3_Drive.mp4" poster="/videos/FLAMEinNeRF/Subj3_thumb.png" controls>
  This is fallback content to display for user agents that do not support the video tag.
</video>
</div>
<br>
<br>
<div class="embed-container" style="position:relative;padding-bottom:41.56%;">
<video  style="width:100%;height:100%;position:absolute;left:0px;top:0px;" src="/videos/FLAMEinNeRF/Subj2_Drive_2.mp4" poster="/videos/FLAMEinNeRF/Subj2_Drive2_thumb.png" controls>
  This is fallback content to display for user agents that do not support the video tag.
</video>
</div>
<br>
<br>
<div class="embed-container" style="position:relative;padding-bottom:41.56%;">
<video  style="width:100%;height:100%;position:absolute;left:0px;top:0px;" src="/videos/FLAMEinNeRF/Subj4_Drive_2.mp4" poster="/videos/FLAMEinNeRF/Subj4_Drive2_thumb.png" controls>
  This is fallback content to display for user agents that do not support the video tag.
</video>
</div>
<br>
<div align="center">
<br>
