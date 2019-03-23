# 機器學習基礎與演算法

[講師投影片Chapter9 ](https://drive.google.com/file/d/1QBUdp_e2OhK0WzaoL-4ZKzlTE9-mMNYg/view)

[講師投影片Chapter10 ](https://drive.google.com/file/d/1vjasef779W2oSD6yQSGBNiS7G3UOiT2a/view)

[資料與程式碼](https://drive.google.com/drive/folders/1RRX1YEI33jxDl-s7h67K1sVrTDdudjhM)

[課程投影片](https://drive.google.com/file/d/1CxXQhzkyvlkAyZ7u1hHK3TNHznRqYXa-/view)

## 非監督式學習 \(Unsupervised Learning\)

1. 只給 Feature x ，從中找到最具代表性的 Feature \(Dimension reduction\)

   1. 只給 Featurex ，從中判斷類別 \(Clustering\)

##### Dimension reduction

• Principal component analysis \(PCA\)

• T-Distributed Stochastic Neighbor Embedding \(t-SNE\)

##### Clustering

• K-means

• Hierarchical clustering

#### [Dimension reduction ](https://www.youtube.com/watch?v=eC5DzAzUbPQ)降低為度

##### Pricipal component analysis \(PCA\)

目的是把高維的點投影到低維的空間上去，並且希望低維空間裡面能夠保持住高維空間點的大部分性質，這裡的性質是點和點之間的關係．

從高維到低維的過程之中，只允許做linear transforms

variance 盡量大，因為讓降維後的資料不要重疊在一起．還可以保持分布狀態

* 實務上我們經常遇到資料有非常多的 features，有些 features 可能高度相關，有什麼方法能夠把高度相關的 features 去除?

* PCA 透過計算 eigen-value, eigen-vector，可以將原本的features 降維至特定的維度

  * 原本 Data 有 100 個 features，透過 PCA，可以將這 100 個features 降成 2 個 feautres

  * 新 features 為舊 features 的線性組合

簡單可解釋性比較高

有新的點可以直接投影下去

[PCA\(主成分分析\)](https://www.jianshu.com/p/4528aaa6dc48)

##### [T-distributed Stochastic Neighbot Embedding T-SNE](https://www.youtube.com/watch?v=IMqKFq7Yj3o)

允許 non-linear transforms

算 P\(x\|x1\) =

算 Q\(z\|x1\)=

Goal：minimize KL-divergence of P and Q

觀察所有倆兩樣板的資料，有新的點加入的時候，不知道如果投影下去

## Clustering

附近的點放在一起

What is similar ?

Euclidean distance

cosin distance

### K-means algorithm

1. 定義有幾個群
2. 隨機選K個點當作是群的資料中心
3. 看過所有的資料點，並找出資料點離哪一個資料中心最近，我們用這個當作每個點是屬於哪一個群的依據
4. 一旦我們決定每個點屬於哪一個群之後，我們可以計算點當中群中心應該在哪裡
5. 重複第三步，因為群中心已經變過了
6. 直到收斂，群中心不在變更

#### K-means for segmentation

#### Hierarchical clustering \(Cluster Dendrogram\)

Agglomerative \(bottom-up\)

• Start with each data point as a cluster

• Merge two closest clusters until only one cluster left

Divisive \(top-down\) 依靠 K-means

• Start with one cluster

• Each step split a cluster until each cluster contains one data point

##### Agglomerative example



#### 階層式分析

* 不需指定分群的數量

1. 每筆資料視為獨立一群

2. 計算每兩群之間的距離

3. 將最近的兩群合併成一群

4. 重複 2,3 直到所有資料合併為同一群為止

* 計算距離的方式有

○ 'complete': cluster 中，最遠兩點的距離

○ 'single': cluster 中，最近兩點的距離

○ 'average': cluster 中，所有點的距離平均

[ 利用 SciPy 实现层次聚类](https://haojunsui.github.io/2016/07/16/scipy-hac/)



#### Clustering vs classification

Clustering: unsupervisor learning algorithm

Classification：supervisor learning algorithm

Chapter 10 總結 \(Summary\)

