# 卷積神經網路 Convolutional Neural Network & 電腦視覺 Computer Vision

[投影片](https://drive.google.com/file/d/1DvyubtmY0oduN3tGqkAnWubuGEkttiX9/view)

[影片播放列表](https://www.youtube.com/playlist?list=PL1f_B9coMEeBDwstxzx6Y7CRu0f6VTcZ3)

1. CNN實戰 in Keras

2. Generator\(Data Augmentation\)

延伸閱讀 \(Optional\):

1. What does CNN learn?

[理論講授投影片](https://drive.google.com/file/d/184Dz2U2cpV682tTPrOXixIQQO7Y5Gm-G/view)

[今日課程投影片](https://drive.google.com/file/d/1ZxcD5EgFYXCHFmXFh_rPXZVTQTlxOpON/view)

[影片播放列表](https://www.youtube.com/playlist?list=PL1f_B9coMEeBtHVc9a1Z9HBUiKHqKO1Wv)

Aug

### 

### 常見CNN模型探討

### 代表性模型

* AlexNet
* VGGNet
* GoogleNet
* ResNet
* DenseNet

## AlexNet

2012 年發表

架構：

5 convolution layers

3 fully connected layers

Five Major contributions:

* Nonlinearity: Rectified Linear Units\(ReLU\) ReLU vs sigmoid 收斂比較快、避免梯度消失問題
* Multiple GPUs
* Local response normalization \(LRN\)
* Overlapping pooling
* Data augmentation & dropout 避免過適\(overfitting\)問題

輸入過於簡單與資料過於複雜都會容易造成 Overfitting 問題

Top1 error：一次只能猜一個答案，算錯就錯了

Top5 error：一次猜五個答案，其中一個猜對就算對

### VGGNet

2014 年發表

CNN 的層數對正確度的關係

3x3 convolution kernels - less parameters

* More non-linearity
* Less parameters to learn
* More numbers of channels
* Stacked convolution layers have large receptive fields

### GoogleNet\(Inception V1\)

2015 年發表

22 leyers

no fully connection layer

12 times lesser parameters than AlexNet

Inception module

Auxiliary classifiers

### Inception module

選擇 filter sizes of 1x1, 3x3 and 5x5

concatenate all feature maps

concatenate one additional pooling path, which is essential to the success of CNNs

觀察小區域特性和大區域特性，為了平衡大小區域特徵，所以採用 pooling 的方式做 concatenate

Linear decrease in feature maps results in quadratic decrease in computation

使用 1x1 的 convolutional layers來降低 feature maps，

降低 feature maps 的數量1/2，學習的數量是原來的4/1，

Global average Pooling 取代 fully connection layers

### Auxiliary classifiers

Deep networks result in vanishing gradients

Auxiliary classifiers are appended

Intermediate layers become discriminative

Intermediate losses alleviate the problem of vanishing graident

在幾層Inception module 之後增加 SoftMax/Loss 加強 Inception module 的學習強度

當要預測時，拿掉中間的 SoftMax/Loss 只留最後的 softmax/Loss



## ResNet

2016 年發表 用來解決訓練網路在深成時所造成的 Gradient Exploding / Vanishing 問題，

可以訓練到1000層以上



The deeper, the better

* Larger receptive field size
* Higher non-linearity
* Better fitting power

Really ?

Performance drops when using an overly deep CNN model

Overfitting ?

* No. Not only testing but also training error increase!
* This is a general phenomenon, observed in many datasets
* it is caused by gradient exploding/vanishing



### Residual module

Learn the residual F\(x\), instead of the desired output H\(X\)

Residual：Difference between the input and the desired output

Shortcuts connections

* A practical way to go deeper
* Inexpensive 1x1 convolutional layers for channel reduction





