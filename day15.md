# 卷積神經網路 Convolutional Neural Network &電腦視覺 Computer Vision

理論講授[ 投影片 ](https://drive.google.com/file/d/184Dz2U2cpV682tTPrOXixIQQO7Y5Gm-G/view)

今日課程[ 投影片 ](https://drive.google.com/file/d/1b5RU9xDDf2xt_dJpVGZmYeM3YAlqQiMJ/view)

[影片播放列表](https://www.youtube.com/playlist?list=PL1f_B9coMEeBHxSasfeBYAT23a1E82b-D)

本日課程:

1. Object Recognition and Detection

2. R-CNN Family

3. Faster R-CNN 手把手

不同的電腦視覺應用

* Fine-grained object recognition 細緻物件辨識
* Object detection 物件偵測
* Semantic segmentation 
* Image super resolution
* Image style transfer
* Action and gesture recognition
* Image matching and co-segemntation

一般性的物件辨識和細緻性的物件辨識困難

* A large class number 處理物件類別很多
* Large intra-class variations 同類別之間的變異性，比如鳥類有不同背景、姿態
* Subtle inter-class variations 微小的跨類別的變異性\(細緻獨有的困難\)比如：不同種種類的鳥

辨識上面的問題最重要的技術就是CNN，可以做到比人類還要好的辨識



## Fine-grained object recognition

### Part-based Method 方法，物件是由多個重要的部分組成

* Appearance of parts 
* Spatial relationships betwwen parts 

Constellation Model\[Fergus et al., 2007\]

Part-based 融入 CNN

### CNN 反向工程

Visualizing and understagding convolutional networks \[Mattew D., and Fergus 2014\]

* Neuron：part detector
* Feature map：the spatial occurrence of certain part 

提出 co-occurrence layer 物件的 part 有沒有共同出現，part 之間的關係

Co-occurrence Layer貢獻層

* Differentiable：the resultant CNN is end-to-end trainable
* Nonlinear across neurons
* Robust：rotation and translation-invariant



CUB-200-2011 資料集



