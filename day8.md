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

[○ XGBoost 詳解 - 中文](https://medium.com/jameslearningnote/%E8%B3%87%E6%96%99%E5%88%86%E6%9E%90-%E6%A9%9F%E5%99%A8%E5%AD%B8%E7%BF%92-%E7%AC%AC5-2%E8%AC%9B-kaggle%E6%A9%9F%E5%99%A8%E5%AD%B8%E7%BF%92%E7%AB%B6%E8%B3%BD%E7%A5%9E%E5%99%A8xgboost%E4%BB%8B%E7%B4%B9-1c8f55cffcc)

[○ XGBoost parameter tuning - 英文](https://www.analyticsvidhya.com/blog/2016/03/complete-guide-parameter-tuning-xgboost-with-codes-python/)

[○ slides from XGBoost author - 英文](https://homes.cs.washington.edu/~tqchen/pdf/BoostedTree.pdf)

#### Stacking





## Practical concerns









