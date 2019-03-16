# 機器學習基礎與演算法

[ ](https://doc-10-a8-docs.googleusercontent.com/docs/securesc/0e6o73khf30bge47v75ur1f0ansg0qb7/hbkigjjjm9spdhr1qgp49psdmg87eo5h/1551852000000/17581372301209011741/15400212421688111872/1xiJegBUNO6vIwDKleslxamYABYGO_DaE?e=download&nonce=bdftdsv7idrii&user=15400212421688111872&hash=21v2ojv6o7dsjb7o42etsnqkmoobfdre)影片播放列表: [影片播放列表 ](https://www.youtube.com/playlist?list=PL1f_B9coMEeB9vVZLAVVY99Q6jUyMxxZ-)

投影片 PDF:[講義一](https://drive.google.com/file/d/1R8GfHT2YYPFM3m2s41vjuEf0FB-eumgt/view)、[講義二](https://drive.google.com/file/d/1JIVR4OvTNxP4v2pVDRk1Qe9vN7aHlmbk/view)

機器學系概論

Traditional algorithm vs machine learning

#### Types of Machine Learning

Supervised Learning\(監督是學習\)\(最多討論、最成熟\)

Unsupervised Learning\(非監督是學習\)

Semi-supervised Learning

Reinforcement Learning

Supervised Learning

* 給一組&lt;input , output&gt; 資料
* 給公司資料，給賺錢資料，預設明年是否賺錢

#### 輸出類別：

* Categorical: classification problem

  ```
    ordinal outputs: small, mediun, large

    Non-ordinal outputs: blue,green, orange
  ```

* Real values:regression problen

* Other types

Traning data: 訓練資料

Test Data: 測試資料

Features: 特徵 input x

Target variable : 目的變數 output y

#### Classification 分類問題

* supervised learning task
* Goal: 給一個特徵 x ，預測c 是什麼類別 give a feature vector x, predicts which class in c may be associated with x
* if \|c\| = -&gt; Binary Classification, if \|c\| &gt;2 -&gt; Multi-class Classification

* Classifier f\(x\) 可以是線性\(linear\)或非線性\(non-linear\)

linear or non-linear

有名的分類模組

* k-nearest neighbor\(kNN\)
* Decision Tree\(DT\)
* Logistic regression
* Support Vector Machine\(SVM\)



#### Regression 回歸

* supervised learning task
* 訓練和預測是回歸問題



#### Over-fitting\(過度分類\) vs under-fitting\(輕度分類\)



小考：

Q:explain the difference between a supervised and unsupervised algorithm

A: 

supervised給的每筆資料中飽含 feature and target variable

unsupervised給的每筆資料中只有 feature 沒有 target variable



Q: Explain the difference between classification and regression

A:

兩個都是 supervised 每筆資料包含 feature and target variable

classification的target variable 型態是 categron variable

regression的target variable 型態是 real number



Q: Classify the normal mails and the junk mail based on the labeled datasets，Supervised or unsupervised? 

A: supervised

Q: Predicting the price of stock? Classification or regression

A: regression





