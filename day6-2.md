# 機器學習基礎與演算法

[ ](https://doc-10-a8-docs.googleusercontent.com/docs/securesc/0e6o73khf30bge47v75ur1f0ansg0qb7/hbkigjjjm9spdhr1qgp49psdmg87eo5h/1551852000000/17581372301209011741/15400212421688111872/1xiJegBUNO6vIwDKleslxamYABYGO_DaE?e=download&nonce=bdftdsv7idrii&user=15400212421688111872&hash=21v2ojv6o7dsjb7o42etsnqkmoobfdre)影片播放列表: [影片播放列表 ](https://www.youtube.com/playlist?list=PL1f_B9coMEeCvbetNGYmW7fWUBSo0-D_i)

投影片 PDF:[講義一](https://drive.google.com/file/d/1-wzKsQIEN3gToiZcpWE41lDq89a4JqHG/view)

[課程投影片](https://drive.google.com/file/d/1fzHUM0mJxE99vK07t2pYVwsDS7Ge6sbh/view)

[資料與程式碼](https://drive.google.com/drive/folders/1RRX1YEI33jxDl-s7h67K1sVrTDdudjhM)



## [Suport vector machines SVM](https://www.youtube.com/watch?v=UrC5qzU0FMA)



#### Linear SVM



Margin distance



Maximum margin



Soft margin and slack variable



#### [Lagrange multiplier and KKT condition](https://www.youtube.com/watch?v=MAjskeeDBpc)



Lagrange multiplier is a strategy for finding the extreme value of a function subject to equality constraints.

對於有 equality constraints 的最佳化問題，事實上我們可以使用 Lagrange multiplier 系統的求解

什麼是equality constraints 的最佳化問題？

我們要最佳化的事 y = f\(x\) ，我們想要找到什麼樣的x，可以最大化f\(x\)，

但是這個x是有限制的 gi\(x\) = 0, i=1,2,3..,m 一個限制或多重限制

ylambda = f\(x\) + lanbda1g1\(x\) + lanbda2g2\(x\) + lanbda m gm \(x\)

lambda i 's are called "Lagrange multipliers"



#### Generalized Lagrange multiplier

Lagrange multipliers is generalized to include the inequality constraints under the Karush-Kuhn-Tucker

如果我們除了 equality constraints，還包括 inequality constraints 的話

那我就要用到generalized Lagrange multipliers

Standard form problem

Minimize f\(x\) subject to gi\(x\) &lt;= 0 \(i=1,2 ..,p\) and hj\(x\) = 0\(j=1,..,m\)

Lagrangian











