# Tech/ Tricks
## Data
### data augmentation
horizontally flipping, random crops, color jittering
### PCA Whitening
reduce dimension  
i.i.d (independent and identically distributed)
### Dataset balancing
#### set weighting for each class
#### OHEM (2016)
[Training Region-based Object Detectors with Online Hard Example Mining](https://arxiv.org/abs/1604.03540)
#### OHEM + sampling
## Dropout
[AlexNet](CNN/index#alexnet-2012)  
solve: overfit
## Regarlization
plenty the weight in loss function  
solve: overfit
## Normalization
[Normalization](basic/normalization.md)  
solve: Internal Covariate Shift
## Skip Connection
[ResNet/U-net](CNN/index#resnet-vs-u-net)
## Residual scaling
if the number of filters exceeded 1000, the residual variants started to exhibit instabilities and the network has just “died” early in the training, meaning that the last layer before the average pooling started to produce only zeros after a few tens of thousands of iterations.  
caling down the residuals before adding them to the previous layer activation seemed to stabilize the training. 
## visual gradient vanishing
[how-to-fix-these-vanishing-gradients](https://datascience.stackexchange.com/questions/28835/how-to-fix-these-vanishing-gradients)