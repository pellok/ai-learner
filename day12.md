# 深度學習

#### Introduction to Deep Learning

[講師投影片](https://drive.google.com/file/d/1F6Xz4b6iDR0iwsScEn_IqNM4gDXhCgDs/view)

[講義](https://drive.google.com/file/d/1IhRLFmpWlglxiPAZ1YJ8jb3Qmpq1jNsm/view)

[影片播放列表](https://www.youtube.com/playlist?list=PL1f_B9coMEeC38AHRAP2XnoffkoCEFV4K)

[程式碼](https://drive.google.com/drive/folders/1sH38d7elXKVpgsJCjPSOvIRa7cZDYDig)



## 神經網路調教

#### 數據前處理

神經網路只吃數字資料，所有非數字資料都要轉換成數字資料

* 順序資料轉數值 

exp: {Low, Medium, High} -&gt; {1,2,3}, 

         {0-17, 55+, 26-35} -&gt; {15,70,30}

* 名目資料轉數值 

exp: {"SugarFree", "Half", "Regular"} -&gt; {1,0,0},{0,1,0},{0,0,1}\(One-hot encoding\)

         台北市南港區... -&gt; 25.04, 121.61\(地址轉換成經緯度\)

* Re-scale 數值資料 \(Loss 等高線\)



