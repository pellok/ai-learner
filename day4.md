# 機率統計

資料與程式碼: [程式碼與練習題解答 ](https://drive.google.com/drive/folders/1uNTCbC_J8Lrnr8tZGuqrVC3K3Jqqdiag)

影片播放列表: [影片播放列表 ](https://www.youtube.com/playlist?list=PL1f_B9coMEeBgVxW4VBXAi_Zp4xzdFLXn)

投影片 PDF:[投影片PDF下載連結](https://drive.google.com/drive/folders/16hpIwZ6dNaD8CcNk4Yvq7jjrVFMTjPYZ)

#### 

#### [hmwu\_StatR-01.1\_BasicStat-Descriptive](https://www.youtube.com/watch?v=dAAkpHCkIWY) 敘述統計

為什麼要學機率統計?

[科學事實與統計思維 \(程開明, 中國統計, 2015年第12期, 24-26.\)](http://www.slstjj.gov.cn/index/ShowArticle.asp?ArticleID=1856)

[我所理解的統計思維](http://blog.sciencenet.cn/blog-242272-1047853.html)

資料屬性：

* Nominal\(名目變數\), Categorical\(類別資料\), discrete：

* Ordinal\(順序\)：

* Interval:

* Ratio\(連續資料\)

資料描述：中心趨勢、分散程度

偏態\(skewness\)系數

峰態\(kurtosis\)係數

[hmwu\_StatR-01.2\_BasicStat-Correlation](https://www.youtube.com/watch?v=BSrzkPP7r-w) 敘述統計

相關係數

Pearson Correlation

Spearman rank correlation

Kendall's tau：兩個變數有沒有一致性

HDD\(High-dimensional data\)高維度資料

HDLSS example

* images圖片
* microarray基因

解法之一：Shrinkage

google Penalized/Regularized/Shrinkage Methods

[numpy 線係運](https://blog.csdn.net/zenghaitao0128/article/details/78715140)[算](https://blog.csdn.net/zenghaitao0128/article/details/78715140)

[線性代數](https://ccjou.wordpress.com/2010/06/18/線性代數的第一堂課-矩陣乘法的定義/)[ 矩陣相乘](https://zh.wikipedia.org/wiki/矩陣乘法)

#### [hmwu\_StatR-02.1\_Probability-Terminology](https://www.youtube.com/watch?v=zkz0XbmTAow) 機率分佈

#### 是以數學函數的方式來表示隨機實驗中，不同的可能結果\(樣本空間之每個元素\)發生的可能性\(機率\)

統計名詞：

* A random experiment 隨機實驗：做一件事情當中，觀察到事情的不確定性，做完之後就知道答案是什麼

* Outcome\(結果\)：做完的結果

* Sample space\(樣本空間\)：所有Outcome所形成的集合

  ```
    例子1: 投擲兩硬幣, 正\(Head\)反\(Tail\)面之樣本空間 S={HH, HT, TH, TT}.
  ```

* Event\(事件\)：樣本空間裡面的子集合

* Trial\(試驗\)：髓機實驗的最小單位

  ```
    例子3: 投擲4枚硬幣的隨機實驗中，每投擲一次硬幣皆是一次「試驗」。
  ```

* Probability \(機率\)：長期執行下來的結果，我有興趣的那個實驗的平均發生的次數多少

* Random variable \(隨機變數\)：把事件對應的一個數線上去

機率質量函數 Probability Mass Function \(非連續型, 離散型\)

* 機率質量函數把每個值對應到機率
* 所有質量和為1

機率密度函數 Probability Density Function \(連續型\)

* 都是大於零的
* 積分起來等於1
* 算機率＝算積分

常用機率分佈的應用

Normal distribution：常態分佈

Log-normal distribution：數值曲log之後常態分佈

Discrete uniform distribution：離散型均勻分布, exp:丟骰子

Binomial distribution：二項式分佈, 成功 or 失敗

Negative binomial distribution：負二項分布, 成功K之前，失敗的次數

Chi-squared distribution：標準常態的平方

累積聚率分配函數CDF\(p\)：隨機機率變數小於某一個數字的機率是多少

分位數Quantiles\(q\)：給你一個x 他的機率是p，反求給你機率p 他的x是多少，常出現在信賴區間

統計改變了世界\[書\]

#### [hmwu\_StatR-02.2\_Probability-Distribution](https://www.youtube.com/watch?time_continue=1&v=gwjlhKIP-9Q) 常見之分佈\(二項分佈、常態分佈\)

伯努利試驗

常態分佈,高斯分佈

以常態機率逼近二項次機率

#### [h](https://www.youtube.com/watch?v=cqtxb9uIFiE)[mwu\_StatR-02.3\_Probability-CLT](https://www.youtube.com/watch?v=cqtxb9uIFiE)

大數法則\(LLN\)：由具有有限\(finite\)平均數μ的母體隨機抽樣，隨 著樣本數n的增加，樣本平均數 越接近母體的 平均數μ

中央極限定理\(CLT\)：由一具有平均數μ，標準差σ的母體中抽取樣本大小為n的簡單隨機樣本，當樣本大小n夠大時，樣本平均數的抽樣分配會近似於常態分配。

[中央極限定理: 樣本平均之抽樣分佈](https://seeing-theory.brown.edu/basic-probability/cn.html)

#### [hmwu\_StatR-03.1\_Estimation-MLE](https://www.youtube.com/watch?v=LjryNwhf8fU) 參數估計

點估計\(動差法、最大概似法、最小平方法\)

概似函數\(The Likelihood Function\)

最大概似估計法\(Maximum Likelihood Estimation MLE\)

點估計步驟：

1. 抽取代表性樣本

2. 選擇一個較佳的樣本統計量當估計式 3. 計算估計式的估計值

3. 計算估計式的估計值

4. 以該估計值推論母體參數並作決策

區間估計

#### [h](https://www.youtube.com/watch?v=GSTZZYKF47g)[mwu\_StatR-03.2\_Estimation-Bayes](https://www.youtube.com/watch?v=GSTZZYKF47g)

貝氏定理

後驗機率 = 可能性 x 先驗機率 / 標準化常量

貝氏估計法

#### [hmwu\_StatR-04.1\_Testing](https://www.youtube.com/watch?v=JPsG6Kurm3E) 假設檢定

假設檢定：我想要知道對一個母體特性的命題，決定一下他和不合理的過程

exp：汽油一公升平均2.5，這一件事情合不合理，怎麼檢驗這個命題正不正確？

方法一：調查全國加油站，一公升的汽油平均多少

方法二：調查一些加油站，對母體推估，抽了一個樣本平均價格2.2，

這2.2根2.5差了0.3到底又沒有差別？

原來的命題到比正不正確？



Hypothesis Testing

虛無假設\(Hull hypotheis\)：H0=2.5

擇一假設\(alternative hypothesis\)：Ha: u &gt;2.5

顯著顏準\(significance level\)\(alpha\)：alpha=0.05，容忍錯誤5%



型一誤差、型二誤差：固定型一誤差尋找型二誤差



p-values

* 定義:在已知\(現有\)的抽樣樣本下，能棄卻 H0\(虛無假設\)的最小顯著水準。\(Reject H0 \| H0 true\)

* 若H0 為真，則檢定統計量出現\(觀察到此樣本\)的可能性。 \(若p-value越小，表示抽樣樣本越不可能出現，因此推翻假設，拒絕H0\)。
* p-value:以現有的抽樣所進行的推論，可能犯typeIerror的機率。 \(若p-value越小，表示拒絕H0不太可能錯，因此拒絕H0\)



Decision Rule ：p-values越小越要拒絕虛無假設，p值越小表示顯著性越高，容易誤用

[林澤民，看電影學統計: p值的陷阱](http://blog.udn.com/nilnimest/84404190)



T 檢定\(t-test\)：

T分佈



Test Homogeneity of Variances

var.test {stats}

bartlett.test {stats}

ansari.test {stats}

mood.test {stats}

fligner.test {stats}

leveneTest {car}



建議使用：

Fligner-Killeen's

Levene's

Levene's is widely used and is typically the default in SPSS

















