# image-to-image

pix2pix -> start point  
LAPGAN, Progressive GAN, pix2pixHD -> higher resolution  
cycleGAN -> unpaired, cross domain  
Augmented CycleGAN, Paired CycleGAN, ComboGAN, StarGAN -> cycleGAN variant for representational learning/ multi. domains  

## pix2pix (CVPR 2017)
[Image-to-Image Translation with Conditional Adversarial Networks](https://arxiv.org/abs/1611.07004) by Phillip Isola, Jun-Yan Zhu, Tinghui Zhou, Alexei A. Efros  
[https://phillipi.github.io/pix2pix/](https://phillipi.github.io/pix2pix/) | 
[Image-to-Image Demo](https://affinelayer.com/pixsrv/)
based on [conditional GAN](/generative_models/GAN_repersentation_learning.html#conditional-gan-2014), with image as conditional&noise input  
![](img/pix2pix_result.png)
dataset: paired image (supervised), e.g. segmentation/edge/map -> real photo, real photo → map
discriminator: PatchGAN which also take conditional as pairs 

## LAPGAN (NIPS 2015)
[Deep Generative Image Models using a Laplacian Pyramid of Adversarial Networks](https://arxiv.org/abs/1506.05751)  
aim for **high-resolution** image via using low-resolution image as condition, similar to residual learning
> In this paper we introduce a **generative parametric model** capable of producing high quality samples of natural images. Our approach uses **a cascade of convolutional networks** within a **Laplacian pyramid framework** to generate images in a coarse-to-fine fashion. 
Note: Could I consider it as GAN plus residual+GAN based super-resolution?
![](img/LAPGAN_sampling_procedure.png)

## DTN (ICLR 2017)
[Unsupervised Cross-Domain Image Generation](https://arxiv.org/abs/1611.02200)  
Domain Transfer Network(DTN) with Identity Loss.  
![](img/DTN.png)
##### Identity Loss
first proposed in Equation 6 of this paper  
> The generator trained with this loss will often be more conservative for unknown content. -- from CycleGAN FAQ

## Two-Way GANs
[Two-Way GANs](two-way_GAN.md)

## Progressive GAN (ICLR 2018)
[Progressive Growing of GANs for Improved Quality, Stability, and Variation](https://arxiv.org/pdf/1710.10196.pdf) by Nvidia  
[Official TensorFlow implementation](https://github.com/tkarras/progressive_growing_of_gans) | [PyTorch implenetation (unofficial)](un-official)  
### Growing
resize + w * conv, increase weighting of convolution to fade smoothly  
fully integrate previous learning result into bigger model  
### Result
<iframe src="https://www.youtube.com/embed/XOxxPcy5Gr4" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

### Compare with LAPGAN
Progressive GAN merge the small model into large model. In inference step, Progressive GAN take features as input, LAPGAN take low-resolution image as input

## pix2pixHD (CVPR 2018)
[High-Resolution Image Synthesis and Semantic Manipulation with Conditional GANs](https://arxiv.org/pdf/1711.11585.pdf) by Nvidia + author of pix2pix  
[Project](https://tcwang0509.github.io/pix2pixHD/)
> We present a new method for synthesizing **high-resolution photo-realistic** images from semantic label maps using conditional generative adversarial networks (conditional GANs). Conditional GANs have enabled a variety of applications, but the results are often limited to low-resolution and still far from realistic. In this work, we generate 2048x1024 visually appealing results with a **novel adversarial loss**, as well as new **multi-scale** generator and discriminator architectures. Furthermore, we *extend* our framework to *interactive visual manipulation* with two additional features. First, we incorporate object instance segmentation information, which enables object manipulations such as removing/adding objects and changing the object category. Second, we propose a method to generate diverse results given the same input, allowing users to edit the object appearance interactively. Human opinion studies demonstrate that our method significantly outperforms existing methods, advancing both the quality and the resolution of deep image synthesis and editing.
![](img/pix2pixHD.png)
### Coarse2fine Generator
### Compare with Progressive GAN
* The main idea of both 2 paper is grow the GAN after training low-resolution. Training small generator first, then use a bigger generator include the small generator.  
* pix2pixHD is supervised/conditional while Progressive GAN is un-supervised. pix2pixHD have a encoder in generator while Progressive GAN start with latent input.
* pix2pixHD is handle low-resolution image feature as residual. Progressive GAN fade-out the previous small model and let the big model continus learning the weight.
* When inference with final model, pix2pixHD input high resolution input image + resized low resolution input image(s). Progressive GAN input size remain (latent random noise).  
Question: What if growing network like Progressive GAN (fade) instead of residual for conditional GAN? Sadly the requirement of training Progressive GAN is high (8 Tesla V100 ;\_;)

## vid2vid (NIPS 2018)
(put in this section because I consider video as sequence of images)
[Video-to-Video Synthesis (Arxiv)](https://arxiv.org/abs/1808.06601) | 
[Video-to-Video Synthesis](https://tcwang0509.github.io/vid2vid/) | 
[github](https://github.com/NVIDIA/vid2vid) - by Nvidia (Includes works of pix2pixHD and SPADE)

## Transferring GANs (ECCV 2018)
[Transferring GANs: generating images from limited data](http://openaccess.thecvf.com/content_ECCV_2018/papers/yaxing_wang_Transferring_GANs_generating_ECCV_2018_paper.pdf)

## GauGAN
### SPADE (CVPR 2019)
[Semantic Image Synthesis with Spatially-Adaptive Normalization](https://arxiv.org/abs/1903.07291) by Nvidia  
### Project
[Live Interactive Demos](https://www.nvidia.com/en-us/research/ai-playground/) | 
[Project](https://arxiv.org/abs/1903.07291) | 
[blog](https://blogs.nvidia.com/blog/2019/03/18/gaugan-photorealistic-landscapes-nvidia-research/)
<iframe width="1173" height="660" src="https://www.youtube.com/embed/p5U4NgVGAwg" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

## Spectral Regularization (CVPR 2020)
[Watch your Up-Convolution: CNN Based Generative Deep Neural Networks are Failing to Reproduce Spectral Distributions](https://arxiv.org/pdf/2003.01826.pdf)  
> Generative convolutional deep neural networks, e.g. popular GAN architectures, are relying on convolution based up-sampling methods to produce non-scalar outputs like images or video sequences. In this paper, we show that **common up-sampling methods, i.e. known as upconvolution or transposed convolution, are causing the inability of such models to reproduce spectral distributions of natural training data** correctly. This effect is independent of the underlying architecture and we show that it can be used to easily detect generated data like deepfakes with up to 100% accuracy on public benchmarks. To overcome this drawback of current generative models, we propose to add a novel **spectral regularization** term to the training optimization objective. We show that this approach not only allows to train spectral consistent GANs that are avoiding high frequency errors. Also, we show that a correct approximation of the frequency spectrum has positive effects on the training stability and output quality of generative networks.