# 深度學習導論

#### Introduction to Deep Learning

[講師投影片](https://drive.google.com/file/d/1F6Xz4b6iDR0iwsScEn_IqNM4gDXhCgDs/view)

[影片播放列表](https://www.youtube.com/playlist?list=PL1f_B9coMEeC_tYQSo6SGRvYc-xqzctRV)

[程式碼](https://drive.google.com/drive/folders/1sH38d7elXKVpgsJCjPSOvIRa7cZDYDig)

#### [簡介](https://www.youtube.com/watch?v=Bko-FyJGXlE)

#### 讓機器擁有知識 - Ontology

Thing - 食品 - has Food Additives - is a Name

* is a Type

  * has Food Item - is a Salt

  * is a Egg

#### 知識與推論 - BDI Agent

B: Beliefs 這個agent 對這個世界的認知

D: Desires 這個 agent 想要達成的目的

I: Intentions 這個 agent 的能力

BDI-Concept - Maper - OWL-Ontology

演化是計算\(Genetic Algorithm\)

你要有辦法把你的演算法的解決方案編碼成一個基因組，然後把演算法的基因組丟到環境去做測試，

測試好的演算法留下來，拿去做突變，突變後在編成基因組，循環上面的步驟，直到很好的解決問題

螞蟻演算法\(Ant Colony Algorithm\)

#### 機器學習

CNN RNN 都是監督式學習

GAN 非監督式學習，本質上是監督式學習

Hierachical Clustering：快速

Center-base Clustering：K-means快速

Density-base Clustering：DB Screem

#### 強化學習 Reinforcement Learning

強化是學習不是learning from data，他是learning from evirement

今天只要告訴機器在這個環境中可以做什麼事情，機器會任意做事情，

回有獎賞機制，作對給分，做錯扣分，長期下來，機器就會知道要做什麼．

嘗試錯誤學習下來，會越來越厲害直到打敗人．

廣義來說強化式學習也是learning from data，但是這個data是自己產生的

不是所有事情都可以，像失敗很重的就不能使用，只能用在可以模擬的環境來學習

像：AlphaZero、ApphaStar

### [深度學習 Deep Learn](https://www.youtube.com/watch?v=gYASL27Hn40)

* 是一種機器學習的方法
* 藉由模仿人類大腦神經元的結構，定義解決問題的Function
* 原本稱為\(類\)神經網路\(Neural Network, NN\)
* 所謂深度學習是一種具有深度\(多層\)的Neural Network

ImageNet Challenge 從照片中辨認資料\(裡面是什麼東西\)

人類的錯誤率是5%，傳統的是25%

2015 已經可以達到3.5%，超越了人類

#### 類神經網路與多層感知機 Neural Network & Multilayer Perceptron

單一感知器Single perceptron \(neuron in NN\)

y-hat = 激發函數\(w1x1,w2,x2...wnxn+b\)

激發函數：也是感知函數，解決所謂的分類問題

#### 線性可分/不可分 問題

深度學習可以解線性不可分問題

Sigmoid Function

一個神經元，就是Logistic Regression \(邏輯式回歸\)

引入多重神經元 與 非線性的激發函數

XOR 問題

#### 多重感知機\(Multilayer Perceptron, MLP\)

* Multiple line or polyline
* Introducing non-linear

輸入的資料經過一層層的神經元打散之後，分別運算最後最後預測

f\(x, theta\) :

theta: weights, bias

找出一組最好的 theta，最好的參數，最適合的參數

什麼叫做好

#### 評估與尋找最佳函數

預測出來的答案和真正的答案對照，比對的時候定義loss function，實際差多少

希望預測結果和實際解果差不多，讓我的loss 最小的最佳解．

Theta\* = argimin L\(theta\)

#### [梯度下降與反向傳播 Gradient Descent & Backpropagation](https://www.youtube.com/watch?v=ZC66no2y_ZI)

假設f只有一個參數w，如何獲取最低 Loss ？

#### 梯度下降 Gradient Descent

##### 反向傳播 - 連鎖率\(Chain Rule\) 與偏微分

##### 連鎖率

y = f\(x\), z = g\(y\) ==&gt; dz/dx = dz\*dy / dy\*dx

要求z對x的微分，先做 "z對y的微分" 再乘上 "y對x的微分"

##### 偏微分

z = f\(x,y\)

x = g\(t\), y = h\(t\)

∂z/∂t = ∂f \* ∂h / ∂h \* ∂t + ∂f \* ∂h / ∂h \* ∂t

∂：d 偏微分符號

反向傳播

Loss Function

∂L /∂ theta = \(∂L \* ∂y-hat / ∂y-hat \* ∂ theta\) - \(∂L \* ∂y-hat \* ∂z / ∂y-hat \* ∂z \*∂theta\)

反向傳播 - Notation

反向傳播 - Loss Function 平均的誤差

L\(theta\) = 1/ R \|\| ∑\(f\(x power of r; theta\) - y power of r \) \|\|

theta = argmin L\(theta\)

#### Backpropagation - 反向傳播

Backword Pass

Backpropagation 是為了算梯度的反方向去下降

#### 超參數

##### Learning rate 控制gradient descent 走的步數

#### Stochastic Gradient Descent \(隨機梯度下降法\)

#### Mini-batch Gradient Descent

#### Mini-batch vs Epoch

#### 梯度消失問題\(Gradient Vanishing\)

解決使用 SGD 造成局部最小值，而沒有找到全域最小值

利用 momentun 克服梯度消失

Momentun

* 先算 gradient
* 加上 monentum
* 更新

Nesterov monentum

* 加上 momentum
* 在算 gradient
* 更新



