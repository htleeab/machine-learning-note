# Pose-to-Body
also see [Video Synthesis](../video/video_synthesis.md)

## Types
A. Train a uniform generator for different videos. Reference appearance frame and pose/motion are input as condition during inference.  
B. Train a generator on frames of **same** video. The appearance is encoded in the model. Only pose/motion input is required during inference.  
Generally, type B seems give nicer result with less artifact, but need to re-train a new model for each traget person. Used in motion re-target papers.
- vid2vid
- Deep Video-Based Performance Cloning
- Everybody Dance Now

## Pose Guided Person Image Generation
[Pose Guided Person Image Generation (NIPS 2017)](https://arxiv.org/abs/1705.09368)  
[python 2.7 + tensorflow-gpu 1.4.1](https://github.com/charliememory/Pose-Guided-Person-Image-Generation)  
![](https://raw.githubusercontent.com/charliememory/Pose-Guided-Person-Image-Generation/master/imgs/Paper-framework.svg)

## PoseWarp
[Synthesizing images of humans in unseen poses (CVPR 2018)](https://openaccess.thecvf.com/content_cvpr_2018/CameraReady/1978.pdf)  
[CVPR 2018 Oral](https://youtu.be/XWr0Fg5XbPs?t=1970) | [Keras](https://github.com/balakg/posewarp-cvpr2018)  
Source	Image	Segmentation + Spatial Transformation + Foreground	Synthesis + Background Synthesis

## VUNet
[A Variational U-Net for Conditional Appearance and Shape Generation (CVPR 2018)](https://openaccess.thecvf.com/content_cvpr_2018/papers/Esser_A_Variational_U-Net_CVPR_2018_paper.pdf)  
[Project](https://compvis.github.io/vunet/) | [tensorflow >= 1.3.0](https://github.com/CompVis/vunet)  
![](https://raw.githubusercontent.com/CompVis/vunet/master/assets/cvpr2018_large.gif)
![](https://compvis.github.io/vunet/images/deepfashion_transfer.png)

## Pose Guided Human Video Generation
[Pose Guided Human Video Generation (ECCV 2018)](https://openaccess.thecvf.com/content_ECCV_2018/papers/Ceyuan_Yang_Pose_Guided_Human_ECCV_2018_paper.pdf)

## vid2vid
[vid2vid (NeurIPS 2018)](../video/video_synthesis.md#vid2vid)  
![](https://github.com/NVIDIA/vid2vid/raw/master/imgs/pose.gif)

## Deep Video-Based Performance Cloning
[Deep Video-Based Performance Cloning (Eurographics 2019)](https://arxiv.org/pdf/1808.06847.pdf)

## Progressive Pose Attention Transfer for Person Image Generation
[Progressive Pose Attention Transfer for Person Image Generation (CVPR 2019)](https://openaccess.thecvf.com/content_CVPR_2019/papers/Zhu_Progressive_Pose_Attention_Transfer_for_Person_Image_Generation_CVPR_2019_paper.pdf)  
[PyTorch 0.3.1 or 1.0](https://github.com/tengteng95/Pose-Transfer)
<p float="center">
	<img src='https://raw.githubusercontent.com/tengteng95/Pose-Transfer/master/imgs/women1.jpg' width="100"/>
  	<img src='https://raw.githubusercontent.com/tengteng95/Pose-Transfer/master/imgs/walkfront.gif' width="100"/>
  	<img src='https://raw.githubusercontent.com/tengteng95/Pose-Transfer/master/imgs/women2.jpg' width="100"/>
	<img src='https://raw.githubusercontent.com/tengteng95/Pose-Transfer/master/imgs/dance.gif' width="100"/>
	<img src='https://raw.githubusercontent.com/tengteng95/Pose-Transfer/master/imgs/women3.jpg' width="100"/>
    <img src='https://raw.githubusercontent.com/tengteng95/Pose-Transfer/master/imgs/dance2.gif' width="100"/>
    <img src='https://raw.githubusercontent.com/tengteng95/Pose-Transfer/master/imgs/women4.jpg' width="100"/>
    <img src='https://raw.githubusercontent.com/tengteng95/Pose-Transfer/master/imgs/dance3.gif' width="100"/>
</p>

## Everybody Dance Now
[EDN (ICCV 2019)](./motion_retargeting.md#EDN) skeleton-to-rendering part
![](https://carolineec.github.io/everybody_dance_now/images/teaser.png)

<!--
## DwNet
[DwNet: Dense warp-based network for pose-guided human video generation (BMVC 2019)]()  
[Python 2, pyTorch 1.0.1 ](https://github.com/UBC-Computer-Vision-Group/DwNet)
![](https://raw.githubusercontent.com/UBC-Computer-Vision-Group/DwNet/master/demo/teaser.png)
-->
