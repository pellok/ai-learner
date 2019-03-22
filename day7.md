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

        使分群變"純"



Split criterion

* Goodness function
* Different algorithms may use different goodness function:

        Information gain\(used in ID3\)

        Gain ratio \(used in C4.5\)

        Gini index \(used in CART\)



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

        Gain\(A\) = Info\(D\) - Infoa\(D\)



範例

問題



#### Gain ratio

* information gain 通常問題：選的 Attribute是那個 attribute 有很多的value的，例如說，沒一個人都有一個唯一的ID，依據information gain 來選，會選到ID來分群，因為沒個的ID都不一樣，可以用Gain ratio 來解決這個問題
* Gain ratio 可以想像成，有做過normalization 的 information gain
* GainRatio\(A\) = Gain\(A\)/SplitInfora\(D\)













