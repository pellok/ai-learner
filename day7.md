# 機器學習基礎與演算法

第一天

資料與程式碼: [程式碼與練習題解答 ](https://doc-10-a8-docs.googleusercontent.com/docs/securesc/0e6o73khf30bge47v75ur1f0ansg0qb7/hbkigjjjm9spdhr1qgp49psdmg87eo5h/1551852000000/17581372301209011741/15400212421688111872/1xiJegBUNO6vIwDKleslxamYABYGO_DaE?e=download&nonce=bdftdsv7idrii&user=15400212421688111872&hash=21v2ojv6o7dsjb7o42etsnqkmoobfdre)

影片播放列表:[ 影片播放列表 ](https://www.youtube.com/playlist?list=PL1f_B9coMEeDnlocZvO4vREgupj3TWhh5)

[課程投影片 PDF](https://drive.google.com/file/d/1MMvIagRphMt_OBg4uUAj_bb4bZt6YEJc/view)

[講師投影片](https://drive.google.com/file/d/14IjJzwiKRqRQ_YKAEMcpgsHwTjvx1c5t/view)

### 

## Decision Trees 決策樹

依據一連串的問題來決定結果，問題有先後順序

#### Select a splitting criterion 分類問題

* 依據 attributes 來分群，查看拿一個分類的比較好，所以我們要找出好 attributes，

  ```
    使分群變"純"
  ```

Split criterion

* Goodness function
* Different algorithms may use different goodness function:

  ```
    Information gain\(used in ID3\)

    Gain ratio \(used in C4.5\)

    Gini index \(used in CART\)
  ```

##### Expected Information \(Entropy\)

什麼是 Entropy，衡量亂度的指標

Info\(D\) = I\(3,2\) = -3/5log\(3/5\)-2/5log\(2/5\) ≈ 0.971 ，比較亂有比較高Entropy

Info\(D\) = I\(5,0\) = 5/5log\(5/5\)-0/5log\(0/5\) = 0，比較純有比較低Entropy

#### Information gain\(Root Know\)

* Expected information \(entropy\) needed to classify a tuple in D

Info\(D\) = - ∑ pi log\(pi\)

pi: probability that a tuple in D belong to Ci

m: number of classes

* 我們使用 A 來區分 Ｄ 產生 分群，分群有多亂 Infoa\(D\) = ∑ \|Dj\|/\|D\| x info\(Dj\)
* Infomation gain: Information Gain by branching on attribute A

  ```
    Gain\(A\) = Info\(D\) - Infoa\(D\)
  ```

範例

問題

#### Gain ratio

* information gain 通常問題：選的 Attribute是那個 attribute 有很多的value的，例如說，沒一個人都有一個唯一的ID，依據information gain 來選，會選到ID來分群，因為沒個的ID都不一樣，可以用Gain ratio 來解決這個問題
* Gain ratio 可以想像成，有做過normalization 的 information gain
* GainRatio\(A\) = Gain\(A\)/SplitInfora\(D\)





#### Gini index



Gini\(D\) = 1- ∑ pi power of 2

pi: 屬於這i 這個屬性的比例



Gain\(A\) = Gini\(D\) - Ginia\(D\)



Exp:

Gini\(D\) = 1- \(9/14\) power of 2 - \(5/14\) power of 2 = 0.459



這三種在實務上好像沒有什麼差別，都差不多，但是如果你的資料有特殊的指標，可以自行使用



#### Overfitting and tree pruning

Decision tree 很容易把每一個資料都單獨分一群



Prevent overfitting

* Pre-prune the tree ：事先規定好樹長什麼樣字，比較簡單，計算量也比較小，

        不同資料對數的限制也不一樣

* Post-prune the tree 不作限制，等之後再修剪掉，計算量比較大，根據訓練資料的不同，

       可以根據資料的特性做一些不一樣的調整

所以用 post-prune 的 test accurcy 效果好一些



Post-pruning considerations 目標考量

最後的樹越小越好，規則簡單

最後的樹 test error 不可以很高

上面兩點互相抵觸，使用下面指標來觀察

砍掉大顆的樹，讓規則簡單，有要讓錯誤率降低，所以要挑選好的大樹砍



a\(ti\) = \(\#error after cut - \#error before cut\) / \#leaves been cut -1 ，數值越小越好

Example of post-pruning





補充：

如果是數字，可以選一個切點，來分類

資料排序之後，查看結果有變化的地方，來當切點



Decision Tree 可以用在 Regression tree 嗎？

Interpretable prediction



 

[Let’s Write a Decision Tree Classifier from Scratch - Machine Learning Recipes \#8 手寫決策數程式碼](https://www.youtube.com/watch?v=LDRbO9a6XPU)













