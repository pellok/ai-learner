# 卷積神經網路 Convolutional Neural Network &電腦視覺 Computer Vision

理論講授 [投影片 ](https://drive.google.com/file/d/1gr_U_FlIT8cbJ35zr5Raf1tNe5x4rgkM/view)

今日課程 [投影片 ](https://drive.google.com/file/d/1pEJ-2RYYwOAIow90JqfaBKRWSZApWYSN/view)

[影片播放列表](https://www.youtube.com/playlist?list=PL1f_B9coMEeDtGJ00o8v9Qg7z0meYcdhB)



# semantic segmentation 語意分割、語太分割

Goal：Label each pixel to one of the predefined classes or background

在給定一些物件類別，假如說給一些類別，給一張圖片，標出類別或什麼都不是

Critical to hight-level vision tasks such as scene understanding robot navigation, and image retrieval



Fully Convolutional Network for Semantic Segmentation\(FCN\) \[Long et al., CVPR'15\]

Fully convolutional network：移除Full connection layer

為什麼要移除Full connection layer？，因為經過全連接層無法保留位置資訊



### FCN 網路結構

* Use AlexNet, VGG 16-layer net, or GoogleNet
* Discarding the final classifier layer
* Convert all fully connected layers to convolutions
* Append a 1 x 1 convolution with channel dimension 21 to predict scores for each of the PASCAL classes.













