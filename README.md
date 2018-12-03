AirBnB image evaluation for adversising using ResNet with Torch 7
============================

## Requirements
See the [installation instructions](INSTALL.md) for a step-by-step guide.
- Install [Torch](http://torch.ch/docs/getting-started.html) on a machine with CUDA GPU
- Install [cuDNN v7](https://developer.nvidia.com/cudnn) and the Torch [cuDNN bindings](https://github.com/soumith/cudnn.torch/tree/R7)

## Training

For Class Prediction

To train on our airBnB dataset located @ /* copy our dataset and configure it with the correct torch configuration so it can be loaded with the Torch ImageNet dataloader. We have already done this and the classes can be configured at this repo /*

Once configured, retrain the pretrained network with  
```
th main.lua -retrain resnet-152.t7 -data datasets/airbnb/ -resetClassifier true -nClasses 3 -nGPU 5
```
In this case we chose to create 3 classes on price point and retrain image net with the images from airbnb based on the price points. Various optimization options determine performance. See various options to configure the various approaches i.e softmax for class prediction across all home images, classification with merged channels, price regression prediction and  linearizing image space across all homes.

## Trained models


#### Single-crop (224x224) validation error rate
Evaluations with various ResNet implementations
| Network       | Top-1 error | Top-5 error |
| ------------- | ----------- | ----------- |
| ResNet-18     | 30.43       | 10.76       |
| ResNet-34     | 26.73       | 8.74        |
| ResNet-50     | 24.01       | 7.02        |
| ResNet-101    | 22.44       | 6.21        |
| ResNet-152    | 22.16       | 6.16        |
| ResNet-200    | 21.66       | 5.79        |

## Notes


