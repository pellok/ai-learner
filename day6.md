# 機器學習基礎與演算法

[ ](https://doc-10-a8-docs.googleusercontent.com/docs/securesc/0e6o73khf30bge47v75ur1f0ansg0qb7/hbkigjjjm9spdhr1qgp49psdmg87eo5h/1551852000000/17581372301209011741/15400212421688111872/1xiJegBUNO6vIwDKleslxamYABYGO_DaE?e=download&nonce=bdftdsv7idrii&user=15400212421688111872&hash=21v2ojv6o7dsjb7o42etsnqkmoobfdre)影片播放列表: [影片播放列表 ](https://www.youtube.com/playlist?list=PL1f_B9coMEeB0uxQwlKLGGyDpI_Xs8iCY)

投影片 PDF:[講義一](https://drive.google.com/file/d/1rl6xs7-2_LPuYmXzJcS8pU8eR2uBSgDJ/view)、[講義二](https://drive.google.com/file/d/1e11A6QbAj2FxEALSVqJXLvg-F_RFlvwu/view)

[課程投影片](https://drive.google.com/file/d/160-WCt5I_m1F3yR3-mzqgW4WlkSaAXty/view)

[資料與程式碼](https://drive.google.com/drive/folders/1RRX1YEI33jxDl-s7h67K1sVrTDdudjhM)

#### [KNN - K-nearest neightbors](https://www.youtube.com/watch?v=0RIJUK0il2I)

在一個分佈圖裡面，要預測的點的K個最接近的鄰居，

計算範圍內的點都是屬於哪一個分類，就預測未知點為那個分類

前處裡：Feature normalization

* Scale to \[0,1\]
* Scale to \[-1,1\]
* Normalized to N\(0,1\)

#### [Overfitting and underfitting in KNN](https://www.youtube.com/watch?v=ryjdPBrGFsM)

How to select K

overfitting and underfitting 的現象

K vs train error vs test errror

K越來越小，K=1 不會有 traning error，但是會有很高的testing error，

這時候就是overfitting 的時候

KNN \(K Nearest Neighbor\)

* K個最近的鄰居

* 近朱者赤;近墨者黑 ○ 孟母三遷

* You are the average of the five people you spend the most time with.

KNN 優缺點

● 優點

* 訓練速度快

* 不用對模型進行泛化

* 也可以做regression

● 缺點

* 預測時速度慢，且佔用很大的記憶體空間

* 需要對feature normalize

* 不適合用在高維度資料



## [Logical Regression](https://www.youtube.com/watch?v=cZ-lAVT80KE)

classification by linear regression 

Linear regress is highly influenced by the extreme values

Fitting an S-shaped function

Logical function y=1/\(1+e power of -\(theta0 + theta1\*x\)\) y最大為1, y 最小為0

sigmoid function

Logical function vs Hyperbolic tangent function\(a.k.a tanh function\)

Logistic vs tanh function



Logistic Regression

* Define f\(x\) = y-hat = 1/\(1+e power of -\(theta0 + theta1\*x\)\) = 1/\(1+ e power of\(theta transfer\)\*x\)

* 找出好的 theta0 and theta1 使得 y-hat\(預測\) 無限接近 yi\(真實\)
* Loss function: cross entropy loss



#### [grandent ascent](https://www.youtube.com/watch?v=RHX62jeV5jg)

Probability and likelihood

P\(y=1\) = f\(x\) = 1/\(1+e power of\(theta transfer\) \*x\)

p\(y=0\) = 1- f\(x\)

P\(y\) = f\(x\) power of y \(1- f\(x\)\)power of 1-y

L\(theta\) = 

Likelihood and log like

為什麼要取log

1. 相加比相乘快
2. 小數相乘會有underflow精確度問題，相加不會變成零



How to find theta?

* Method 1: 沒有 closed form solution
* Method 2: grandient descent 找出目標函數的最小值，

       我們要找出最大值所以使用 -l\(theta\)

* Method 3: gradient ascent 找出目標函數的最大化值

       l\(theta\) is a convave\(反過來的碗公\) function

       

#### Gradient ascent

Derivative of logistic function

g\(x\) = 1/ 1+e power of -x = \(1 + e power of -x \) power of -1

g‘\(x\) = g\(x\)\(1-g\(x\)\)



#### Derivation of the log likeilood function

l\(theta\) = ∑{ Xij\(y - y-hat\)}



#### Cross entropy and log-likelihood of classifition problem

* Maximize the log-like-lihood function

theta = argmax\(∑{ yilog\(yi-hat\) + \(1-yi\)log\(1-yi-hat\) }\)

* This is the same as minimizing the netgative of the log-likelihood function

theta = argmmin\( - ∑{ yilog\(yi-hat\) + \(1-yi\)log\(1-yi-hat\) }\)

#### log-likelihood 最大 = 負的log-likelihood\(這就是cross entropy loss\) 最小



#### Regularization to avoid overfitting 

new goal:

theta := argmax\[ ∑{ yilog\(yi-hat\) + \(1-yi\)log\(1-yi-hat\) - sita/2\|\|theta\|\| power of 2 \]

penalize high weigth , like we did in linear regression!



Derivative of l\(theta\)



#### Stochastic gradient descent 

相似的我們可以使用 GD、SGD、mini-batch GD來解logistic regression

#### Multi-class logistic regression

Two classes

Multiple classes\(1,2,...,C\) : softmax function

P\(y=c\) = e power of thetac power of T \* x/ ∑ e power of thetac power t \*x











       



