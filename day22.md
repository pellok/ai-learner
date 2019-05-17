# Generative Adversarial Network 對抗式生成網路

[講師投影片](https://drive.google.com/file/d/1R3IEINqOfAsfwE7T5nJFghHz3dyWn0Cy/view)

[資料與投影片](https://drive.google.com/file/d/1g_E98S0u-gB6iCG7NZLKPooVlDoMKX1k/view)



## 1.Introduction of GAN

* GAN原理理論說明
* Vanilla GAN 程式實作



[演講影片](https://www.youtube.com/watch?v=oE6Xe5Cyy7Y)

[gan-zoo](https://github.com/hindupuravinash/the-gan-zoo)



## Generation by GAN

### Basic Idea of GAN

#### Generator ：it is a neural network , or a function

輸入vector -&gt; Generator -&gt; 輸出Image\(High demensional vector\)



#### Discriminator：it is a neural network , or a function

輸入 Image -&gt; Discriminator -&gt; scalar\(判斷圖片像不像\)



#### Algorithm

* Initialize generator and discriminator
* In each training iteration

Step 1：Fix generator G and update discriminator D

Step 2：Fix discriminator D and update generator G 

Step 3：交替使用 Step1 and Step2 重複很多次，越多次越好



\(Variational\) Auto-encoder

Auto-encoder vs GAN

### Theory behind GAN

* A generator G is a network. The network defines a probability distribution Pg

Noral Distribution -&gt; Generator G -&gt; Pg\(x\) &lt;-&gt; Pdata\(x\)

G\* = argminDiv\(Pg, Pdata\), Divergence between distributions Pg and Pdata

How to compute the divergence?透過 Discriminator 來衡量

Example Objective Function for D

V\(G,D\) = Ex~Pdata\[logD\(x\)\] + Ex~Pg\[log\(1-D\(x\)\)\], \(G is fixed\)

Training D\* = argmaxV\(D,G\)









Conditional Generation





Unsupervised Conditional Generation





Relation to Reinforcement Learning









