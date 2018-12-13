AirBnB image evaluation for adversising using ResNet with Torch 7
============================

## Requirements
See the [installation instructions](INSTALL.md) for a step-by-step guide.
- Install [Torch](http://torch.ch/docs/getting-started.html) on a machine with CUDA GPU
- Install [cuDNN v7](https://developer.nvidia.com/cudnn) and the Torch [cuDNN bindings](https://github.com/soumith/cudnn.torch/tree/R7)

## Training

For Class Prediction

To train the raw airBnB dataset located @ **[AirBnB raw data](https://drive.google.com/open?id=1NLDIJslIrmhSi_-HT6ZhzID2rU1oKxFu)** copy our dataset and configure it with the correct torch configuration so it can be loaded with the Torch ImageNet dataloader. We have already done this and the classes can be configured at this repo /*

To gather your own data for airBnB published data dumps, please find our  **[data collector repository](https://github.com/kevinjesse/AirBnB)**

The pre split 80/20 train test dataset with three price point classes can be found @ **[here](https://drive.google.com/open?id=109WmQqOUCVNJLJ5H8p_pFoX9T_YFpgSh)**

Once configured, retrain the pretrained network with  
```
th main.lua -retrain resnet-152.t7 -data datasets/airbnb/ -resetClassifier true -nClasses 3 -nGPU 5
```
In this case we chose to create 3 classes on price point and retrain image net with the images from airbnb based on the price points. Various optimization options determine performance. See various options to configure the various approaches i.e softmax for class prediction across all home images, classification with merged channels, price regression prediction and  linearizing image space across all homes.

## Trained models


#### Single-crop (224x224) validation error rate
Evaluations with various ResNet implementations

| Network       | Top-1 error | Top-2 error |
| ------------- | ----------- | ----------- |
| ResNet-50     | 52.649      | 24.707      |
| ResNet-100    | 52.649      | 24.707      |
| ResNet-152    | 52.649      | 24.707      |


## Notes

**[Preliminary results ](https://github.com/kevinjesse/airbnb_deep/blob/master/Visual%20Score%20Generation%20and%20Comparison%20Metrics%20for%20Advertising.pdf
)** 
