# 機器學習基礎與演算法

### Chapter 8 Practical concerns

[講師投影片Chapter7 ](https://drive.google.com/file/d/1lG1s5a9JpBPLXJGTT2Tz2PdGd9Ag1gpO/view)

[講師投影片Chapter8 ](https://drive.google.com/file/d/1iQvYeHTLVu3GjbXuPLzhQFa9VQWPJw4Y/view)

[課程投影片 ](https://drive.google.com/file/d/1y4HOH31mUaZ4peeFrWD3vvL2vxgw-UcB/view)

[資料與程式碼 ](https://drive.google.com/drive/folders/1RRX1YEI33jxDl-s7h67K1sVrTDdudjhM)

[播放清單](https://www.youtube.com/playlist?list=PL1f_B9coMEeDPl3dZ_ZmoDB1A2gjPa3hg)

### [集成學習 \(Ensemble learning\)](https://www.youtube.com/watch?v=HvJsTAQ4mXY)

Ensemble learning 試圖以一個系統化的方式將好幾個supervisor learning model 的方式結合在一起，希望結合的結果可以截長補短，得到比較好的結果

為什麼 ensemble 可以比較好：三個臭皮匠，勝過一個諸葛亮

分為三大類

* Bagging：我們把training data重新做sample，來產生不同組的training data，根據不同組的training data，即使我們使用相同的演算法來training 也會得到不同model

* Boosting：根據每一筆training data資料的難易度給不同的權重，什麼是難或簡單呢?首先我們先train 一個 basic learner，然後根據basic learner預測的結果的對錯，來當作是一筆難或簡單的資料，對於難的資料我們加強他的權重，再重新訓練難的資料，讓她把難的資料分對，重複以上動作

* Stacking：有好幾個basic learner，都有待解決問題的一些判斷，把這些output的機率，檔成新的input feature，然後重新learn 一個新的model，新的model 的output 當成依據．

#### [Bagging \(Booststrap aggregating\)](https://www.youtube.com/watch?v=tkYoWXHf1Ok)

Bootstrap： 隨機抽取樣本\(random sample with replacement\)

Bootstrap aggregating：

* 重複 bootstrap m 次
* 對每一個 sample train 一個 model ：每個model 都是 weak learner
* 結合 models 來預測： 趨向 strong learner

##### Random forest

使用 bagging + randomized feature set

[Random Forests - The Math of Intelligence \(Week 6\)](https://www.youtube.com/watch?v=QHOazyP-YlM) 線上教學 Random forest python 程式教學

#### [adaboost：Adaptive Boosting](https://www.youtube.com/watch?v=G5sSqvOr7QA)

Boosting ：

Weighted combination of models

Assign different weight to different samples

EXP

##### Gradient boosting machine \(GBM\) 梯度提身機

##### adaboosting 的延伸

[GBM介紹](https://docs.google.com/presentation/d/12rnECA-on7yaGl9T8d9nVZP4nFuG16fkXRDlKaY0fBw/preview?slide=id.p48)

[intro to gradient boosting](https://machinelearningmastery.com/gentle-introduction-gradient-boosting-algorithm-machine-learning/)

XGBoost \(eXtreme Gradient Boosting\)：終極大殺器

XGBoost is an implementation of gradient boosted machine but add some features

XGBoost vs GBM

Earlystop in XGBoost

[Kaggle Winning Solution Xgboost Algorithm - Learn from Its Author, Tong He ](https://www.youtube.com/watch?time_continue=7&v=ufHo8vbk6g4)

[○ XGBoost 詳解 - 中文](https://medium.com/jameslearningnote/資料分析-機器學習-第5-2講-kaggle機器學習競賽神器xgboost介紹-1c8f55cffcc)

[○ XGBoost parameter tuning - 英文](https://www.analyticsvidhya.com/blog/2016/03/complete-guide-parameter-tuning-xgboost-with-codes-python/)

[○ slides from XGBoost author - 英文](https://homes.cs.washington.edu/~tqchen/pdf/BoostedTree.pdf)

#### Stacking

## Practical concerns 實際問題

### Data Preproc

##### 

##### Consider Transforming features

* Min-Max scaling：線性範圍轉會到 range \[-1,1\] or \[0,1\]
* Standardize：scale each feature to N\(0,1\)
* Robust scaling：是為了防止少數的極端值，讓scale 的效果不好
* Thresholding：選定一個threshold，大於threshold 就當1，小於就當0
* Apploying log or exponential function：

##### Why scaling ?

* For KNN, scaling prevents the distances scores being dominated by few features

* For linear regression, logistic regression, SVM, scaling helps the optimization

* For descision tree and random forest, scaling or not is not important

##### Why log or expoential ?

##### Missing values 缺值

if type of the feature is categorical

* replace the missing values with the most frequent value

if type of the features is numerical

* replace the missing values with the mean or median

some more adveanced techniques

* predict the missing values , usually by interprolation and extrapolation

##### Imbalanced classification

##### 正樣本和副樣本比例懸殊很大

common techniques for imbalanced dataset:

* Under-sample the majority class 數量比較多的那一類 取一部份smaple出來
* Over-sample the majority class 數量比較少的 sample 重複一些樣本

  ```
   在數量少的那一類隨機抽出一個樣本，再放回去，讓數量變多
  ```

* 混用上面兩種

#### Selecting hyper-parameters 如何選擇參數

Example of the hyper-parameters

* K in KNN

* C in the regulatized linear classification

* Step size in gradient descent

Strategies

* Grid search：列出 hpyer-parameter 的可能值，試過所有排列組合
* Random search：隨機挑選 hyper-parameter 的組合，重複n幾次
* Bayesian optimization：我們先嘗試一組，依據結果在好壞，來挑選附近或其他不同的

Random search 可能會比 Grid search 好

##### 衡量選得好不好

把data 分成三個部分 Training / validation / test datasets

使用training data 搭配不同的 hyper-parameter 訓練很多組 model

使用 validation data 來評估好的 hyper-paramenter 的model效果好

在使用好的hyper-parameter 和資料 \(Training+validation\) 來訓練新model

Testing data 來測試新的model 得到Acuuray

#### Multi-class classification 多元分類

Some models can handle multi-class：

* KNN

* Decision trees

* Neural networks

Leaverage on binary classifiers

* One-vs.-rest
* One-vs.-one

##### One-vs.-rest

Train a single classifier for each class

如果要訓練 Target labels: "red", "blue", "gree"

分別訓練：

f1：is"red" or not "red"

f2：is "blue" or not "blue"

f3：is "gree" or not "gree"

y-hat = arg max fk\(xi\) 看f1,f2,f3, 拿一個分數比較高，就選最高分當作我們的預測

##### One-vs.-one

Training：for a k-nary classification problem, one trains C\(K,2\) classisfiers

如果要訓練 Target labels: "red", "blue", "gree"

f1：is "red" or "blue"

f2：is "red" or "gree"

f3：is  "blue" or "gree"

#### Model selection

##### 

##### Bias vs variance

The test error comes from 錯誤來原

* Bias：f\(x\) 到假說空間之間的距離，如果模型的假說空間不包含 f\(x\) ，預測不會準
* Variance：我們的data取樣有所偏差，所以模型沒有辦法學習完整的資料，所以會造成誤差
* Noise：人為錯誤



Model complexity vs error



Training size vs error



Data size vs model complexity

資料大小和模組完整



SOP



Model selection summary

* Domain knowledge important
* Model complexity is important
* Data size is important









