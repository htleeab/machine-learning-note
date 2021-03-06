# Image Deblurring
Many [super-resolution](super-resolution.md) papers also handle deblur
## Type of blur or noise
* Motion Blur
* Out of Focus
* Low-resolution
* Encoding Noise
The first one related to video
## Learning a convolutional neural network for non-uniform motion blur removal (CVPR 2015)
## Blind Image Deconvolution by Automatic Gradient Activation (CVPR 2016)
## DeepDeblur (CVPR 2017)
[github](https://github.com/SeungjunNah/DeepDeblur_release)
* new dataset: [REDS](https://seungjunnah.github.io/Datasets/reds) 
## Self-paced Kernel Estimation for Robust Blind Image Deblurring (ICCV 2017)
## blur2mflow (CVPR 2017)
[From Motion Blur to Motion Flow: a Deep Learning Solution for Removing Heterogeneous Motion Blur](https://donggong1.github.io/docs/blur2mflow_cvpr17.pdf)
[Project](https://donggong1.github.io/blur2mflow)  
estimate motion flow and use then estimated motion flow to recover the clear image
![](https://donggong1.github.io/projects/blur2mflow/framework.jpg)
![](https://donggong1.github.io/projects/blur2mflow/net.png)

## DeblurGAN (CVPR 2018)
[DeblurGAN: Blind Motion Deblurring Using Conditional Adversarial Networks](https://arxiv.org/pdf/1711.07064.pdf)  
[pyTorch](https://github.com/KupynOrest/DeblurGAN)| [Keras re-implementation](https://github.com/RaphaelMeudec/deblur-gan)  
0.2fps for 1080p on GTX1080 Ti
Requirement of running pre-trained weights:
```
pyTorch version 0.3.1
torchvision 0.2.0
torchtext 0.2.3
revert NINJA commit (b15a520d660e4366e10bd1110398c731da1f1f6c)
python3 test.py --dataroot <folder> --model test --dataset_mode single --learn_residual --loadSizeX 1920 --loadSizeY 1080 --resize_or_crop ''
```

### DeblurGAN-v2 (ICCV 2019)
[DeblurGAN-v2: Deblurring (Orders-of-Magnitude) Faster and Better](https://arxiv.org/abs/1908.03826)  
[pyTorch](https://github.com/TAMU-VITA/DeblurGANv2)
* Framework: introduce [FPN](/CNN/object_detection/object_detection.html#fpn-cvpr-2017) to image restoration
* Backbone: use [Inception-ResNet-v2](/CNN/models.html#resnet-2015-cvpr-2016) for quality, [MobileNet](/CNN/light-weight_models.html#mobilenet-v2-cvpr-2018) for speed  
**test pre-trained inception**: Result of debluring video motion blur is quite good, speed also improved, 2.4fps for 1080P on GTX 1080Ti  
[feature/video_inference](https://github.com/htleeab/DeblurGANv2/tree/feature/video_inference) support video inference :)  
But there is some [purple artifact](https://github.com/TAMU-VITA/DeblurGANv2/issues/18) not fixed even the issue is closed :(

## Video Debluring
[Video Debluring](../video/video_deblurring.md)
