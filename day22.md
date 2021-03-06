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

#### Example Objective Function for D

V\(G,D\) = Ex~Pdata\[logD\(x\)\] + Ex~Pg\[log\(1-D\(x\)\)\], \(G is fixed\)

Training D\* = argmaxV\(D,G\)

Can we use other divrgence? \[Sebastian Nowozin, et al., NIPS,2016\]

### Issues and Possible Solutions

* JS divergence is not suitable
* ### Wasserstein distance

WGAN

V\(G,D\) = max {Ex ~ Pdata\[D\(x\)\] - Ex ~Pg\[D\(x\)\]}

#### Tip：Improve Quality during Testing

1.Image Normal Distribution 縮少  &gt; Smaller Variance

2.Mode Collapse 開始產生一樣的資料

3.Mode Dropping

#### Tip：Ensemble

#### Objective Evaluation 衡量GAN效能的方法

#### Inception Score \[Tim Salimans, et al., NIPS 2016\]

## Vanila GAN

生成手寫辨識

## Conditional Generation

[投影片](https://drive.google.com/file/d/1P5mWI9gTPFfGqmtjgIrOJp_fggMgXptn/view)

控制輸出

#### Text - to - Image

* Traditional supervised approach

Conditional GAN - Discriminator

Image - to - Image ：Image translation or pix2pix

GAN + L1

Conditional GAN - Video Generation

Sound - to - Image

需要聲音和圖片的對應關係，網路上有很多影片\(聲音+圖片\)

Conditional GAN - Image - to -label

Multi-label Image Classifier = Conditional Generator

Conditional GAN - Speech Recognition

Domain Adversarial Training

## Unsupervised Conditional Generation

最常用的是 Image style transfer

Disco GAN

Dual GAN

Cycle GAN



Projection to Common Space

Cycle Consistency

Semantic Consistency



Speech Style Transfer聲音轉換



Wasserstein GAN\(WGAN\) Earth Mover's Distance



## Relation to Reinforcement Learning









