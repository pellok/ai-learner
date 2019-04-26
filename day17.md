# 遷移學習\(Transfer Learning\)

[理論講授投影片下載 \(PDF\)](https://drive.google.com/file/d/1iQHZH5U_cTuwTDvxOec_DgDYmdtCK7Bo/view)

[理論講授 影片播放列表 \(YouTube\)](https://www.youtube.com/playlist?list=PL1f_B9coMEeB4GBkfyB_0xzbYAVcb6gOt)

[影片播放 下午 播放列表\(YouTube\)](#)

[今日課程 投影片下載 \(PDF\)](https://drive.google.com/file/d/1SwRHsUjOHpYBOgWOmWscqy92tKzXjjyq/view)

## 主要課程

1. Model Fine-tuning

2. 遷移學習實作 in TensorFlow

延伸閱讀\(Optional\)

1. Multitask Learning

2. Domain-adversarial training

3. Zero-shot Learning

4. Self-taught learning

### 什麼是 Transfer Learning ? 借用經驗

假如你現在手上有一些根你要訓練的沒有相關的Data ，

你能不能用這些沒有直些相關的Data來幫助我們做一些事情

exp:

你要做貓跟狗的分類，但是你有一些資料是分類大象和老虎，或是你有招財貓和高飛狗的圖片

你要訓練的是台語的資料，但是你台語的資料很少，你能不能用其他語言的資料來幫助台語的訓練

Transfer Learning 有很多的方法

#### Model Fine-tuning

Source Data -&gt; Label

Target Data -&gt; Label

複製模型的參數當作初始參數，再用自己的訓練資料進行微調

\(借用的參數會被改變\)

任務描述：

* Target Data 目標資料 \(有資料、有答案\) &lt;= 很少
* Source Data 資源資料 \(有資料、有答案\) &lt;= 很多

舉例：\(監督\) speaker adaption

* Target data： audio data and its transcriptions of specific user
* Source data：audio data and transcriptions from many speakers

Idea：training a model by source data, then fine-tune the model by target data

把訓練好的Source Data 當作初始資料味給 Target Data

* Challenge：only limited target data, so be careful about overfitting

#### 

#### Conservative Training

#### 

#### Layer Transfer

Source Data -&gt; Label

Target Data -&gt; Label

只借用模型的部分神經曾參數，並在訓練的過程中凍結改層參數

現在有用 Source Data 訓練好的一個 model ，你把 model 裡面某幾個 layer 拿出來，

直接 copy 到新的 model 裡面去，接下來呢，你用你的Target data 只去訓練沒有 copy 的 Layer

比如：你只保留一個 layer 是沒有 copy 的 source data，只去訓練那個layer就好，

1. Only train the rest layers \(prevent overfitting\)
2. Fine-tune the whole network \(if there is sufficient data\)

3. Which layer can be transferred\(copied\)?

4. Speech：usually copy the last few layers

5. Image：usually copy the first few layers

注意：使用pre-trained model 時，記得模型架構、資料輸入大小，都要跟對方的一樣喔

### Multitask Learning

Source Data -&gt; Label

Target Data -&gt; Label

在 Fine-tuning 裡面我們 care task domain 做的好不好

在 multitask 裡面我們 care source and task 同時把它做好

怎麼做呢？

The multi-layer structure maks NN suitable for multitask learning

資料有共通性，前面幾個 layer 是共用的

資料沒有共通性，只有中間幾個layer共用

Multitask Learning 很適合用在多語言的語音辨識，前面共用\(人類說\)後面分開不同語言

例如 中翻英、中翻日、中翻韓，輸入都是中文，所以前面幾層共用

#### Progressive Neural Networks

## Domain-adversarial training

Source Data -&gt; Label  -&gt; Training data

Target Data -&gt; Unlabeled  -&gt; Testing data

Training data and Testing data  is mismatch

這邊希望做到的事情是，前面的 Feature extractor 他可以把 domain 的特性去除掉，

這招叫Domain adversarial ，

增加一個 Domain classifier

像是 GAN ，Too easy to feature extractor

Feature extractor 要騙過 Domain classifier 和滿足 Label predictor

Lable predictor 想要做的是分類的正確率越高越好 Maximize label classification accuracy

Domain classifier 想要做的是正確的預測domain的分類 Maximize domain classification accuracy

Feature extractor 想在做的是improve label predictor，同時想要 minimize domain classification accuracy

陷害隊友的分法就是在 feature extractor 和 domain classifier 之間 增加 gradient reversal layer

Domain classifier 一定要奮力掙扎，把 Feature extractor 逼到極限，把 domain feature 移掉

## Zero-shot Learning

Source Data -&gt; Label  -&gt; Training data

Target Data -&gt; Unlabeled  -&gt; Testing data

Training data and Testing data  is different tasks

判斷cat and dog 和 判斷 馬和草泥馬



In speech recofnition, we can not have all possible words in the source \(training\) data.

在語音上很常遇到 Zero-shot 問題，語音行常遇到沒有看過的

我們怎麼解決這個問題呢？ 

不要直接去辨識屬於哪一個字，我們直接去辨識的是一對聲音屬於哪一個目標\(forni\)就好

我們辨識的單位不要定義成word，定義成 forni 就好，

然後我們在做一個 forni 和 word的對應的關係表，我們就稱為 dictionary 字典，

在辨識的時候只要辨識出 forni 再去查表，forni 對應到哪一個 word



在影像上怎麼做？

辨識圖片有哪一些屬性，依據每一個動物去學習動物的屬性

當遇到沒看過的動物的時候，可以判斷出基本屬性



#### Attribute embedding + word embedding

Embedding Space 



#### Zero-shot Learning Loss Function











