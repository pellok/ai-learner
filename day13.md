# 卷積神經網路 Convolutional Neural Network & 電腦視覺 Computer Vision

[講師投影片](https://drive.google.com/file/d/1IfQYf8W--pwqPBUdM5kByFbMrFm8rCDL/view)

[講義](https://drive.google.com/file/d/1lJO_6uqcKUGfD1c1p5Y0-fF9edcCQ2kd/view)

[影片播放列表](https://www.youtube.com/playlist?list=PL1f_B9coMEeA6JFKq8n-FtvI5UVMhj3YV)

本日課程:

1. 電腦視覺入門

2. CNN原理與介紹

延伸閱讀 \(Optional\):

1. Before LeNet

2. CNN Application

3. OpenCV

CV電腦介紹，Filter\(kernel\) 功能介紹，使用Filter可以讓圖片平移、模糊或變銳利等

電腦視覺的應用

1. CV：物件識別 object recognition ML：multiple kernel learning
2. CV：影像切割 Image segmentation ML：graphical model
3. CV：人臉偵測 Face detection ML：multi-task boosting
4. CV：動作辨識 action recognition ML：low-rank reconstruction 利用RGB+Deep 深度和人的骨架
5. CV：人流預測 multi-view people counting ML：transfer learning 利用不同攝影機不同視角來做資訊交流
6. CV：影像比對 image matching ML：energy minimization
7. CV：精細類別分類 fine-grained object recognition ML：CNNs with co-occurence layer
8. CV：patch descriptor learning ML：CNNs with adaptive learning rate
9. CV：手是辨識 gesture recognition ML：DNNs with adaptive hidden layer
10. CV：人臉年齡估計 face age estimation ML：CNNs for hierarchical regression
11. CV：影像共同切割 image co-segmentation ML：Unsupervised CNNs

CNN

* Convolution neural networks\(CNNs\)
* Representative CNN models
* CNN-based computer vision applications

物件辨識：給定一張影像，判斷裡面有哪一些物件

Training phase步驟：

image collection ：收集資料，要辨識什麼東西最收集什麼影像圖片

feature extraction：原始圖片要處理物件特徵，萃取出物件特徵\(這一部份決定關鍵\)

classifier training：訓練物件分類器support vector machines \(SVMs\)

trained classifier：訓練

Testing phase 步驟

test image

feature extraction

trained classifier

prediction

取影像特徵的方法：

* SIFT \[Lowe, IJCV'04\] 被引用4萬多次，已一個影像點為中心，附近的項數的Graiden和強度和方向取特徵
* HoG \[Dalal & Triggs, CVPR\] 被引用2萬多次，有效的取得影像輪廓
* Constellation model \[Fergus et al., CVPR'03\] 被引用2千多次，特徵由若干的區塊組成，以及這些part的幾何對應位置
* DPM\[Felzenszwalb et al., PAMI'10\] 他的強項是可以用機器學習來學習特徵

可以針對沒個要辨識的圖片手動定義要特徵，但是當類別很多的時候，很難每一個都手動定義



### Conventainal approaches vs Deep learning

影像特徵擷蠻困難的，

在傳統的機器學習是經過兩階段的過程

1. 人工選擇合適的影像特徵\(特徵選取\)

2. 再把影像特徵輸入到分類器學習\(分類器學習\)

#### 使用 Deep learning/End-to-end learning/Feature learning 後變成一個步驟，而且都是機器自己學習

Deep learning = Learning hierarchical representations

low-level Feature -&gt; mid-level Feature -&gt; high-level Feature -&gt; Trainable Classifier







