# 遷移學習\(Transfer Learning\)

[理論講授投影片下載 \(PDF\)](https://drive.google.com/file/d/1iQHZH5U_cTuwTDvxOec_DgDYmdtCK7Bo/view)

[理論講授 影片播放列表 \(YouTube\)](https://www.youtube.com/playlist?list=PL1f_B9coMEeB4GBkfyB_0xzbYAVcb6gOt)

[今日課程 投影片下載 \(PDF\)](https://drive.google.com/file/d/1SwRHsUjOHpYBOgWOmWscqy92tKzXjjyq/view)

## 主要課程

1. Model Fine-tuning

2. 遷移學習實作 in TensorFlow

延伸閱讀\(Optional\)

1. Multitask Learning

2. Domain-adversarial training

3. Zero-shot Learning

4. Self-taught learning

### 什麼是 Transfer Learning ?

假如你現在手上有一些根你要訓練的沒有相關的Data ，

你能不能用這些沒有直些相關的Data來幫助我們做一些事情

exp:

你要做貓跟狗的分類，但是你有一些資料是分類大象和老虎，或是你有招財貓和高飛狗的圖片

你要訓練的是台語的資料，但是你台語的資料很少，你能不能用其他語言的資料來幫助台語的訓練

Transfer Learning 有很多的方法

#### Model Fine-tuning

任務描述：

* Target Data 目標資料 \(有資料、有答案\) &lt;= 很少
* Source Data 資源資料 \(有資料、有答案\) &lt;= 很多

舉例：\(監督\) speaker adaption

* Target data： audio data and its transcriptions of specific user
* Source data：audio data and transcriptions from many speakers

Idea：training a model by source data, then fine-tune the model by target data

把訓練好的Source Data 當作初始資料味給 Target Data

* Challenge：only limited target data, so be careful about overfitting

#### Conservative Training

#### 

#### Layer Transfer

現在有用 Source Data 訓練好的一個 model ，你把 model 裡面某幾個 layer 拿出來，

直接 copy 到新的 model 裡面去，接下來呢，你用你的Target data 只去訓練沒有 copy 的 Layer

比如：你只保留一個 layer 是沒有 copy 的 source data，只去訓練那個layer就好，

1. Only train the rest layers \(prevent overfitting\)
2. Fine-tune the whole network \(if there is sufficient data\)

3. Which layer can be transferred\(copied\)?

4. Speech：usually copy the last few layers
5. Image：usually copy the first few layers

#### Layer Transfer - Image





