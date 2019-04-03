# 深度學習

#### Introduction to Deep Learning

[講師投影片](https://drive.google.com/file/d/1F6Xz4b6iDR0iwsScEn_IqNM4gDXhCgDs/view)

[講義](https://docs.google.com/presentation/d/19P48Q2sdMMmhbwH2kdKut6EHEtyhgtRweuQTQFuxX64/edit#slide=id.g4c0faa7db0_0_0)

[影片播放列表](https://www.youtube.com/playlist?list=PL1f_B9coMEeC38AHRAP2XnoffkoCEFV4K)

[程式碼](https://drive.google.com/drive/folders/1sH38d7elXKVpgsJCjPSOvIRa7cZDYDig)

## [梯度下降與反向傳播](https://www.youtube.com/watch?v=ZC66no2y_ZI)\(Backpropagation & Gradient Descent\)

將誤差反向由輸出層往輸入層傳遞\(Backpropagation\)，逐層獲得梯度然後藉由梯度下降\(GD\)調整神經元權重

直到錯誤率最低，機器就成功學會如何辨識一隻貓了

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



