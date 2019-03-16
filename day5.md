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

### Regression 回歸

Notions

* Features x
* Target y
* Prediction y^
* Parameter  sita

## Linear regression 線性回歸

#### 單一 feature y = sita0 + sita1 x

sita1  =

sita0 =

objective function

#### 兩個 feature x1, x2

y = sita0 + sita1 x + sita2 x平方

#### 多個 Feature x1,x2...,xn: multiple linear regression

Close from solution

#### Gradient decent 移動調整 sita 的方法

a: learning rate

a : 在0~1之間

shrink a as k becomes larger

gadient decent 是不段的迭代來產生新的sita i的，什麼時候終止呢？

* sita 值趨緩或者不進步，甚至變差了
* 當traning error 很小了
* 我們已經到達事先定義好的數字了
* 已經到達事先定義好的時間了

#### 

#### Close from solution vs Gradient decent

空間複雜度：

Close from solution：比較大

Gradient decent：比較小

運算複雜度：

close from solution：O\(\)

Gradient decent：O\(Tnd\)

結論：數據大時要使用Gradient decent會更有效率

有時候不一定會有Close from solution，

但是可能可以使用Gradient decent來解



#### One-hot encoding

如果原本的feature 不是線性的，就可以用一些人工的方式讓feature 變成線性



#### 觀察 Overfitting ，解決 Overfitting 使用 Regularization

L2-regularization \(Ridge regression\) 平方

L1-regularization \(Lasso\) 絕對值

怎麼取 landa — 做實驗 像 Cross validation

通常不使用  Unregularized linear regration，因為結果容易overfitting training data

常用的是 Ridge and Lasso

On Regularization 的 Ridge, Lasso and Elastic-net時機

* Ridge : Good if many features have small /mediun sized effects
* Lasso：Good if only a few features with a medium/large effects，容易讓 sita 變成0，相當於沒有作用
* Elastic-net 介於上面兩者之間

解釋 Ridge 和 Lasso 查別，為什麼Lasso 會讓 sita 變成0

Stochastic gradient descent \(SGD\)

一筆筆拿出來算，每次都更新 sita 值

#### GD vs SGD

Steps:

GD: fewer steps

SGD: more steps

Computation of each step

GD: look throught all the training instances

SGD: look only one training instance

#### SGD 的優缺點：

優點：

當資料量大時，比較快

支援線上學習

有時候可能可以跳過 local minimun 問題

缺點：

當我們在到達最低點時，可能會在附近跳動

#### Mini-batch gradient descent ： 一次選一些資料決定GD

#### GD vs SGC vs mini-batch GD

GD：看完全部資料才更新一次

SGC：看一筆資料更新一次

mini-batch GD：看b次資料更新一次

sun of scroll

super of **squared**

hyper parameter 操參數\(人工給定的參數\)



Convex function



### 評估成效 

#### Mean Square Error\(MSE\)

相式方法：Root Mean Squared Error \(RMSE\)

批評： not a normalized measur , 容易受極端值影響



#### Mean Absolute Error \(MAE\)

受極端值影響

#### Media Absolute Error \(MedAE\)

比較不受極端值影響



#### R2 score 

分數為1，效果很好，理想值

分數為0，效果像 Mean Model

分數為-1，model 效果很差







