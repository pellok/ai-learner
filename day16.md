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

#### Deconvolution

如果有沒使用 deconvolution 結果會很差，因為解析度下降太多，要從解析度低的還原到解析度高的地方，基本上是辦不到的，這邊使用前一層的資訊拿到做處理，這樣就可以還原比較清楚．

#### 

## Object Instance Segmentation

a. Image classification ：圖片裡面有什麼，偵測物件\(有人、狗、羊等\)

b. Object localization：除了偵測有什麼物件，並框出物件\(方框\)

c. Semantic segmentation：偵測、切割出物件\(pixel描輪廓\)

d. Instance segmentaion：偵測、物件前後景切割，並標示個別物件

#### Mask-RCNN \[He et al. ICCV'17\]

* Instance Segmentation
* Two Stage Faster R-CNN + FCN

理論講授 [投影片 ](https://drive.google.com/file/d/1gr_U_FlIT8cbJ35zr5Raf1tNe5x4rgkM/view)

今日課程 [投影片 ](https://drive.google.com/file/d/1GJLX5mm85cTvNdx5DsdvK7sZTj7fNuhp/view)

[影片播放列表](https://www.youtube.com/playlist?list=PL1f_B9coMEeCiJeQN_w00Irur8YnNzfPX)

### YOLO\(You only look once\)

* A bref introduction of one-stage detecto

什麼是 Two-stage detector?

將 object detection 分為兩步驟：localization & classification

什麼是 One-stage detector?

end to end training 一次搞定所有任務

We frame object detection as a regression problem to spatially separated bounding boxes and associated class probabilities.

1. resizes the input image to 448x448
2. runs a single convolutional network on the image 
3. thresholds the resulting detections by the model's confidence

#### Loss Function

一個"loss"的架構以及問題

一張圖的輸出有 7x7個長度為30的 tensor

* 8:2 個 bbox 的 x,y,w,h
* 2:2 個 bbox 的 confidence\(是不是object\)
* 20:20 個類別的條件機率

可預見的問題：

* 8 個 bbox & 20 個 類別的 Error 不可相提並論
* 一個 grid 只會預測 2 個 bbox, 而且只會有一類 =&gt; 靠很近 object detect 效果不好
* 不同大小的 bbox, 小 bbox 篇一點比 大 bbox 篇一點更難接受，但在 sum-squared error loss 一樣
* 同一類 object 新的長寬比例效果不好
* 小 object 的 localization error\(小的物件定位效果不好\)

### [YOLO9000 Better, Faster, Stronger](https://pjreddie.com/darknet/yolo/)

#### [YOLO9000: Better, Faster, Stronger论文笔记](https://www.jianshu.com/p/2d88bdd89ba0)



Why does 1 x 1 conv help?



AP explaination



