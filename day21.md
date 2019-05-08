# Kaggle進階技巧 \(上\)

[理論講授 影片播放列表 \(YouTube\)](https://www.youtube.com/playlist?list=PL1f_B9coMEeDtAPmOMeqU4AQ70FywR1lP)

[今日課程 投影片下載 \(PDF\)](https://drive.google.com/file/d/1BdWY3e8vt3esk5Qn9yr6z_nJX6pn8hCI/view)

ch1概論

ch2預處理

ch3-1 數值特徵處理

ch3-2 類別特徵處理

ch3-3 其他進階特徵工程

## 1. Kaggle 概論

因為有競賽所有比較的標準，提供一個學習的平台

Why Kaggle - 最容易學習與應用 - 最具權威與知名度

* 程式碼共享：Kernel制度

* 豐富的資料集\(DataSet\)

* Google 收購並維護

* 參與者最廣泛

## 2. 預處理

#### 填補缺失值 - 什麼是缺失值

* 整條Column都缺失，直接刪除

* 整個Row都缺失，直接刪除

* 零星缺失值

#### 如何填補：

##### 數值特徵：

* 0：缺點是可能會混淆其他本來就是0的數值
* -999：用某個正常情況下不會出現的數值代替，但是選得不好可能會變成異常職
* Mean：平均數
* Median：中位數，跟平均數相比，不會被異常值干擾針對

##### 文字特徵

* Model：眾數，最常見的值
* 改成Others之類的值

##### 使用其他欄位輔助：可以依據常識來填值

#### 特徵縮放 - \[複習\]標準化 / 最大最小化

* 特徵縮放：平衡特徵間的影像力，如果不平痕，可能會影響到後續預測

* 標準化\(Standardization\)：計算 z-score，讓數據的mean為0、variance為1

* 最大最小化\(MinMaxScaler\)：把數據縮放到\[0,1\]或\[-1,1\]的區間

#### 特徵縮放 - 標準化 / 最大最小化 的使用時機

* 標準化：對SVM、Logistic regression或其他使用 squared loss funtion 的演算法來說，需要標準化
* 最大最小化：如果已經去除極端值或沒有極端值，建議使用最大最小化
* 至於Tree-Based的演算法，基本上都不需要標準化或最大最小化，因為對特徵縮放不敏感

## 3.特徵工程

### 3-1 數值特徵處理

##### 去除離群職\(Outlier\) - 為何要去離群職？

* 標準化或最大最小化都是現性轉換，都無法拉近離群值
* 不去除離群職就做標準化或最大最小化，會嚴重壓縮非離群職的資訊

#### 去除離群職\(Outlier\) - 如何去除離值

* 直接刪除：有時光是刪除離群值就有效果
* 限縮資料範圍：將離群值限制在範圍邊界上，如果資料非離群值欄位多，通常以保留盡可能多的資料

#### 去除偏態 - 為何要去除偏態？

* 當數值離群的比例相當大時，不能單純刪除離群值，必須全範圍調整
* 若不調整偏態，平均值失去代表性

#### 去除偏態 - 如何去除偏態

#### 常見的做法有log/sqrt/box-cox/rank

* Log\(取對數\)：處理偏態較大的資料
* Sqrt\(開根號\)：處理偏態較小的資料
* box-cox 分佈：使用 lambda參數混合前兩者去偏態方式\(lambda=0是log，lambda=0.5是sqrt\)
* rank：講資料依照大小順序重新編碼

##### 注意：log 與 box-cox 轉換數入值均不可為0，因此常用log1p取代log

#### 含雜訊數值資料的處理 - 裝箱法\(Binning\)/離散化

* 雜訊：量測變數中的隨機錯誤或偏差
* 處理方式：裝箱法：以區間標籤取代原數值，降低雜訊影響，數值型資料類別化，與原資料共存

#### 統計數值：

* 特殊數得計數：0的數量、NaN的數量、負數的數量
* 列統計值：min、max、median、skewness...等
* 列相似性：cosine similarity

#### \[進階\] 高斯對應\(Rank Gauss\)

* 欄位內容為名次/百分等級，改如何轉換為合理特徵？
* 作法 - 高斯對應：將名次/百分等級，對應到常態分佈累計機率值\(CDF\)的反函數
* 前提：假設實際分佈為常態分佈

### 3-2 類別特徵處理

* 標籤編碼\(Label Encoder\)：將欄位內不同類別，對應到相異整數
* 獨熱編碼\(One Hot Encoder\)：將欄位內不同類別，對應到相異欄位

#### 標籤編碼 / 獨熱編碼 - 哪一個比較好？

* 標籤編碼：資料資訊密度高，計算快，樹狀模型使用標籤編碼，也會有不錯計算效果
* 獨熱編碼：資料每一欄位分開，數值的大小有意義，比較適合非樹狀模型的計算
* 綜合來說：獨熱編碼太過稀疏，記憶體與計算時間負荷重，預設採用標籤編碼
* 計數編碼\(Count Encoder\)：把單一類別的出現次數，視為特徵，注意：次數可能為零\(只出現在Test Set\)、非常態分佈，建議使用np.log1p\(\)去除偏態

```
train['cate_cnt'] = train['cate'].groupby(train['cate']).transform('count')
```

#### 3-3 其他進階特徵工程

#### \[進階\] 平均值編碼\(Mean Encoding\)

* 依造類別目標值的平均值當作編碼，稱為平均值編碼\(例如：房產預測中，依造同一行政區的房產平均當作預估基準\)
* 前提：訓練集與測試集數據分佈相似

```
averages = train.groupby('cat')[target].agg(["mean"])
Train['cat'+'_avg'] = train['cat'+'_avg'].map(averages)
Test['cat'+'_avg'] = test['cat'+'_avg'].map(averages)
```

#### 

#### \[進階\] 平均值編碼的正規化

* 因為平均值編碼預測與訓練目標完全相同，非常容易overfitting，所以要做正規化
* 幾種正規化作法：1.使用平滑化\(Smoothing\)、2.使用K-Fold做Target Encoding3. 加入雜訊
* GatBoost：內建的文字行\(Categorical\)特徵就是用平均值編碼做

#### \[進階\] 嵌入式編碼\(Embedding Encoding\)

* 當單一欄位類別太多時，一般來說沒有很好的方式編碼，只能用雜揍編碼\(Feature Hash\)降低計算時間，但效果通常不好．
* 希望能將類別對應到n個數字，能抽取有意義特徵，又不像獨熱編碼稀疏
* 常見的情形分為兩類：1. 推薦系統、2.自然語言處理中的文字坎入\(Word Embedding\)

#### \[進階\] 自編碼\(Auto Encoder\)

* 使用訓練資料本身\(通常是影像，也可以是非監督資料\)當作目標值：用類神經相接，最中間一層刻意減少神經元數量，若能訓練成功，則前半可視為壓縮器
* 自編碼很常應用在半監督或非監督的前處理，可以再壓縮器後街分群\(非監督\)或其他ML模型\(半監督\)
* 使用類神經網路將資料降維

#### \[進階\] 葉編碼\(Leaf Encoder\) + Random forest

* 原有特徵透過Tree Based 訓練，進行內部的interaction 當作新特徵
* sklearn, tree.apply\(\)
* Xgboost API 使用 xgb.predict\(pred\_leaf=True\)

## 4.特徵選擇

#### 4-1 特徵組合

* 最簡單的創造新特徵的做法：將既有的特徵做加、減、乘、除、根號運算，做出新特徵
* 問題是有沒有必要？Ans：依照領域知識與資料性質而定
* 兩個或多個數值特徵組合

#### 領域知識，例如計程車費率預測：

* 其中與答案相關度高的四個資料欄位：上車/下車 的 經度 / 緯度
* 很明顯：將經緯度當作平面座標，起終點的平面距離
* 經緯度不同長的知識
* 上面兩個都是領域知識，特徵組合的必要性與領域知識相關

#### 群聚編碼\(Group By Encoder\)

* 前面我的提過平均值編碼\(Mean Encode\)，但這是類別行特徵對目標值做平均，如果對另一個特徵平均，我們成為群聚編碼
* 兩者差異1. 平均值編碼：直接對目標平均，很準容易Overfitting 2. 一個類別特徵對另一個數值特徵平均，是結合兩值，不容易Overfitting\(但可能沒有什麼用\)
* 類型特徵與數值特徵組合

不一定只能用平均：Std/Mode/Median/Max/Min/Skew都可以

### 4-2 特徵篩選

* 特徵組合式增加特徵，而特徵篩選是減少特徵，兩者合作可以增加精準度並降低細算時間，不相衝突

特徵篩選有三大類方法：

* 過濾法\(Filter\)：決定評估方式，並刪除低於門檻的特徵
* 包裝法\(Wrapper\)：根據一定法則，逐步加入特徵或逐步刪除特徵\(例如：RFE\)
* 嵌入法\(Embedded\)：根據機器學學習型運算結果，決定刪除的特徵

常用的做法：

* 相關係數過濾法
* L1\(Lasso\)嵌入法
* 梯度提升機\(Gradient Boost Machine\)嵌入法

相關係數過濾法：

* 將相關係數取絕對值較小的特徵刪除
* EDA，繪製相關係數熱圖，有助於暸解特徵與特徵間相關性之外，也可以獲得個別特徵的重要度
* 相關係數過濾法計算快，但準確度有限\(容易受共線性影響\)

L1\(Lasso\)嵌入法：

* 由於 Lasso 擬合\(fit\)後，大部分的係數會為0\(python 會顯示很小的值\)，所以特徵塞選就是刪除係數為0/很小的特徵
* 計算時間與效果都屬於中等\(能排除共線性\)，但能需調整參數，且效果未如下一個提到的梯度提升機好

梯度提升機\(Gradient Boost Machine\)嵌入法：

* 梯度提升機擬合\(fit\)後，每棵樹分支點使用的特徵統計次數，次數越高重要性越高

* 準確性：由於梯度提升機原本就是高準確率的做法

* 泛用度：除了刪除不重要的特徵之外，前幾名特徵也適合當作特徵組合的候選人

* 速度改良：近幾年新一代的機器學習算法：Xgboost、lightGBM、CatBoost都是基於梯度提升機改良，因此速度慢的問題也不太明顯了

* 特徵重要性：最近都以梯度提升機為主流，還有其他的樹狀模型方式

特徵太多先用L1篩選掉一些之後使用梯度提升機挑選重要性

## 模型驗證

訓練集\(train set\) / 測試集\(test set\) 的分割

* 絕對不可以重複
* 不可有統計特徵洩漏

三種分割方式

* 切分\(Hold-Out\)
* K折交叉驗證\(K-Fold cross validation\) sklearn.model\_selection.KFold，資料量大於5000的非深度學習
* 留一交叉驗證\(Leave One Out cross validation, LOO\)，資料級少，小於千筆
* 時序移動視窗驗證\(Time Series Moving Window Validation\) 
* 真實資料 &gt; Test Set &gt; Validation set &gt; Train Set



Kaggle 上的分割策略\(Split Strategy\)

一般來說，自己跑參的 cross-validation 分數 \(Local CV\) 提升，公開排行榜上 的分數 \(Public LB\) 也應該隨之提升

萬一 Local CV 與 Public LB 差異很大，原因可能是 : 

* 數據太少
* 是否 Overfitting
* Splitting 策略出錯 : 按照分布抽樣
* Train/Test 分佈不同 : 無解

用 RandomSearchCV 取代 GridSearchCV

* 珍惜時光
* 集成困難
* 不會陷在局部最佳解

良心建議：除了跑 RandomSearchCV / GridSearchCV外，特徵工程往往是關鍵，盡量嘗試多試試新特徵

## 集成

#### Blending

* Blending 是將原理差距很大的模型輸出，加權後形成新的輸出，結果常常有可能高於混合前的分數
* 迴歸型競賽：Blending 往往很有效
* 分類型競賽組合的前提：Metric 是否是 Convex
* Thumb of Rule：Tree / Non-Tree / NN
* Kindly remind：競賽人數高過三千，通常是組合競賽
* 將單一模型的預測結果，當作混合的初始值，是在predict層級混合的方法

#### Stacking 

* 將單一模型的預測結果，當作下一層的新特徵，是在fit層級混合的方法
* 因為是在fit層混合，每一步驟都需要考慮 Train 與 Validation 不可重複的問題，比較複雜







\[附錄\] 補充資料
