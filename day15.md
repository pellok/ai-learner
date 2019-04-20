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



## Object detection 物件偵測

目的：

1. Recognition\(What?\)識別
2. Localization\(Where?\) 位置，使用定界框，框出物件



#### R-CNN Regions with CNN Features

\[Girshick et al., CVPR'15\]

第一個使用NN來解 Object detection

Proposal extraction：Using selective search\[Uijlin et al., IJCV'13\]，使用有效的方法選出大約2000個框框，這些框框轉乘CNN可以吃的格式再去做分類問題，CNN分類完2000個框框之後就可以定義出物件了．

Compute CNN features in the layer 'fc7' of Caffe CNN

Region classification：linear SVMs or a softmax classifer

Regression-base bounding box refinement 找出定界匡之後，但是不是那麼準確，使用回歸的方式微調

為甚麼要用CNN來做物件偵測？

PASCAL VOC 比賽 ， mAP\(%\)物件偵測率，在2015 年 使用 CNN 來做物件偵測有大幅度進步



#### Fast R-CNN 優化 R-CNN

在 R-CNN 使用 Selective search 找出 2000 個左右的 Bounding box ，已pixel 來看，同時屬於3、4百個Bounding box，每一個bounding box 又丟掉 CNN裡面做分類問題，這是高度重複的運算，如果可以解決高度重複問題，就可以加速Object detetion 問題，使用內插法

Apply fully convolutional network to the whole image

ROI pooling：each proposal is pooled into a fix-size feature map 

Classification with a softmax layer

Regression-based bounding box refinement

在訓練上面加速了8倍，加快了圖片偵測速度到0.32秒



#### Faster R-CNN \[Ren et al., NIPS'15\]

上面兩個方法都是使用 selective search ，這個變成了問題，

作者提出Region proposal network\(RPN\)來取代 selective search

Region proposal network\(RPN\) 有效降低 proposals 數量

* After the last conv. layer
* produces proposals

GPU acceleration is allowed











