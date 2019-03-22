孔令傑

OR、賽局理論

EDA各種應用



業界專案：

手機維修資料分析



料件耗用預測

- 要快



如何減低存貨成本？

- 需要好的訂補貨政策

- 需要好的需求預測 



本專案：做手機料件的維修好用預測，越準越好！



資料

1. 產品生命週期

2. 銷售數據有關連

3. 有一些時段是突然下降\(連假\)



## 料件時間序列：

* 從料件浩用的歷史資料出發
* 考慮三種直觀的時間序列方法

1.HW 指數平滑法\(Holt-Winters Exponential smoothing\)

2.回歸\(Regression\)

3.現行改良法\(Modified Current Method\)



[Smoothing method](https://zh.wikipedia.org/wiki/%E7%A7%BB%E5%8B%95%E5%B9%B3%E5%9D%87) 移動平均線: 在實際上很受歡迎，數字平滑對供應鏈比較好．

moving average:前n天的平均，預測明天，比較n哪一個比較好

Exponential Smoothing 指數移動平均： alpha 是前一期的權重



#### 誤差衡量

三種常見的誤差衡量公式：

* MSE = ∑\(f - xt\) power of 2 /n ，如果要選小誤差就選MSE
* MAE = ∑ \|ft - xt\| /n
* MAPE = ∑



存貨成本

缺貨成本



#### 公式選則：

* 單一料件內的方罰比較 MAE
* MAPE



## 產品時間序列法



生醫具產品歷史資料，預測產品送修量

統計各個產品料件耗用歷史分佈



#### 單品預測匯總法

統計各產品的銷售後送修日數歷史分佈

























