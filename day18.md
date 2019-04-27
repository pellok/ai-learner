# 遞迴神經網路與序列模型

[理論講授投影片下載 \(PDF\)](https://drive.google.com/file/d/1tBUn-uCBX7Q1p6yEgGLsRIVnIfn9kJPN/view)

[理論講授 影片播放列表 \(YouTube\)](https://www.youtube.com/playlist?list=PL1f_B9coMEeAaZ1-Cgakm4HeYx6YTE70R)

[今日課程 投影片下載 \(PDF\)](https://drive.google.com/file/d/1t0o0S6ITrRVrFT2KQghgpYsXVFoyoLuK/view)

課程內容

1. DNN 與 RNN 理論講解

2. 快速回顧 RNN & LSTM

3. Tensorflow 實作 RNN



標準的神經網路

一層神經網路矩陣表示法

Convolutional Neural Network\(CNN\)

Recurrent Neural Network\(RNN\)

1 .我們先問一個問題

2. 反正就是要學個函數 X -&gt; F -&gt; Y

3. 準備訓練資料 訓練資料、測試資料

4. 架構我們的神經網路 

5. 學習Loss function L\(theta\) -&gt; 

基本上就是用 gradient descent、

因神經網路的特性叫backpropagation



### Recurrent Neural Network RNN

一般的神經網路一筆輸入和下一筆是沒有關係的，

也就是說輸入的順序變了，輸出還是一樣的

RNN會偷偷把上一次的輸出也當這一次的輸入．

exp：我們想股市明天的收盤價，也會需要前幾天的資料



#### RNN Cell



#### RNN 的應用

1 .對話機器人 \(注意這樣的模式，每次輸入和輸出都不是固定的長度！\)

2. 翻譯

3. Video Captioning 生成影片敘述

4. 生成一段文字

5. 畫一半的圖完成它

6. 情意分析 \(正評、負評\)



其實輸入不一定要文字，是影片\(一張一張的圖\)也是可以的，輸出還可以是文字，

最常見的大概是讓電腦說影片中發生什麼事













