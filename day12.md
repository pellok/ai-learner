# 深度學習

#### Introduction to Deep Learning

[講師投影片](https://drive.google.com/file/d/1F6Xz4b6iDR0iwsScEn_IqNM4gDXhCgDs/view)

[講義](https://drive.google.com/file/d/1IhRLFmpWlglxiPAZ1YJ8jb3Qmpq1jNsm/view)

[影片播放列表](https://www.youtube.com/playlist?list=PL1f_B9coMEeC38AHRAP2XnoffkoCEFV4K)

[程式碼](https://drive.google.com/drive/folders/1sH38d7elXKVpgsJCjPSOvIRa7cZDYDig)

## 神經網路調教

#### 數據前處理

神經網路只吃數字資料，所有非數字資料都要轉換成數字資料

* 順序資料轉數值 

exp: {Low, Medium, High} -&gt; {1,2,3},

```
     {0-17, 55+, 26-35} -&gt; {15,70,30}
```

* 名目資料轉數值 

exp: {"SugarFree", "Half", "Regular"} -&gt; {1,0,0},{0,1,0},{0,0,1}\(One-hot encoding\)

```
     台北市南港區... -&gt; 25.04, 121.61\(地址轉換成經緯度\)
```

#### Re-scale 數值資料

兩個輸入數值差距很大，會造成 數值大的輸入端的W，W修正對Loss 影響較大

Loss 等高線

不同的scale 的weights 修正需要不同的learning rates

相同scale下，loss 等高線會接近圓形，收斂會比較快，節省訓練時間

#### Re-Scale - Normalization

每個特徵分別進行正規化

調整每個輸入特徵作使其具備相同的分佈\(例如 平均值為0 , 標準差為1的常態分佈\)

有做 re-scale 收斂速度比較快

#### Re-Scale in Hidden Layer

每一個Hidden Layer，再輸入的地方都做 Re-Scale ，

如果沒做會造成internal covariate shift的問題，如果要避免要降低learning reate，

但是降低learning rate 會造成訓練變慢．

#### Batch Normalization

針對給的Batch，計算該Batch的平均值µ與表準差

做完平均值µ與表準差，會讓辛苦學習到的又被壓縮在同一個範圍，

我們不喜歡這樣的變化，所以我們再額外增加一個beta和gama來放大縮放

什麼是beta和gama呢？

做完BN的數值會再乘上beta，再加上 gama，

gama、beta是使用學習\(GD\)得到的

#### Batch Normalization in Testing Stage

* 測試及資料沒有batch 概念，因此其BN所需的平均值和表準差來自訓練資料集

* 但是直接計算整個訓練資料過程中的每一層每個神經元輸出的平均值和表轉差，數據量太大，非常難算

* 折衷辦法，在訓練過程中，每個Batch 分別計算，然後計算其移動平均，

  ```
     如此訓練完成時可以會得一個可供測試資料及使用的平均值和標準差
  ```

### Why Batch Normalization

* 減少internal covariate shift 問題
* 依照 activation function的特性，BN可以減少梯度消失/爆炸 的問題

#### 常見的激發函數\(Activation Function\)

* Sigmoid
* tanh
* ReLU
* Leaky ReLU
* Maxout
* ELU 

分類問題常用的激發函數Softmax

#### 常用的 Loss Function - For Regression Problems

* Mean squared error
* Mean absolute error
* Mean absolute percentage error
* Mean squared logarithmic error
* R2

#### 常用的 Loss Function - For classification Problems

* binary crossentropy\(logloss\)
* categorical crossentropy
* F1-Score

### Loss Function 挑選原則

Classification 問題 以 cross-entropy 搭配輸出層使用 softmax

Regression 問題用 mean absolute/squared error

特定問題可以定義特定 loss function，如

* 針對分類問題客製化 F1-Score

* 針對回歸問題客製化 R2

* 針對 unbalanced dataset 定義 penalty



### 常用的 Optimizer

* SGD – Stochastic Gradient Descent

* Adagrad – Adaptive Learning Rate

* RMSprop – Another Adaptive Learning Rate optimizer

* Adam – RMSprop + Momentum

* Nadam – Adam + Nesterove Momentum



### 什麼是 Overfitting 過度擬和

訓練資料越來越好，測試資料越來越差，代表有overfitting，

就像給學生題目和答案，給學生學習，

再拿學生沒看過的題目給他作答，看他回答得好不好．



#### 避免 Overfitting 的方法 - Regularization

限制 weight 的大小

Loss = ∑\(y - \(b+ ∑wixi\)\) + alpha\(regularizer\)

L1 norm = L1 = ∑\|w1\|

L2 norm = √∑\|w2\|



#### Early Stopping

可以早點停下來



#### Dropout

在訓練過程中隨機disable 一定比例的連結\(將weight 暫時設為零\)

因為訓練得太好，讓他變笨一點

Dropout 可視為一種終極的 ensemble 方法

N個 weight 會有 2的N次方 network structures



#### 何謂 Model Ensemble

三個臭皮匠勝過一個諸葛亮



Dropout & Model Ensemble

























