# Python 資料處理及探索分析

影片播放列表: [影片播放列表 ](https://www.youtube.com/playlist?list=PL1f_B9coMEeCqFRgymsH6aZJg-BW_tBWU)

投影片 PDF:[投影片PDF下載連結](https://drive.google.com/file/d/147IuYb3Q5Bea-aZdvyz2aLjpBQ3h6KfO/view)

練習題下載：[連習題下載](https://drive.google.com/file/d/1U3Xj2V2FekxqGetDGjDNvatKFYvu5z9k/view)

#### [Python\_Numpy](https://www.youtube.com/watch?v=GxdDFtz9KrM)

axis 多維度，列\(axis=0\) or 行\(axis=1\)，先列後行

```
[[1,2,3],
 [4,5,6]]
```

create ndarray

Attributes of ndarray

ndim 幾行 the number of axes\(dimesions\) of the array

shape - 幾列 the dimesions of the array

size - the total number of elements of the array

dtype - the type of the elements of the array

Axes reshpe 變行

```
np.zeros(3), np.zeros(2,3)
np.ones(3), np.ones(2,3)
np.identity(3)
x = np.arange(6).reshape(2,3)
x[1,2]
x[:,1:]
x[:, ::2]
```

Boolean / Mask Index

```
x = np.arange(6)
condition = x<3
x[condition]
x[condition] = 0
```

Concatenate 合併 array

```
a = np.array([[1,2,3], [4,5,6]])
b = np.array([[7,8,9]])
np.concatenate((a,b), axis=0)
#array([[1, 2, 3],
#       [4, 5, 6],
#       [7, 8, 9]])

c = [[0],[0]]
np.concatenate((a,c),axis=1 )
#array([[1, 2, 3, 0],
#       [4, 5, 6, 0]])
```

Basic Operations 基本計算

```
import numpy as np
a = np.array([[1, 2], [3, 4]])
b = np.array([[5, 6], [7, 8]])
print(a + b) # array([[6, 8], [10, 12]])
print(a - b) # array([[-4, -4], [-4, -4]])
print(a * b) # array([[5, 12], [21, 32]])
print(a / b) # array([[0.2, 0.33333333], [0.42857143, 0.5]]
print(a - 1) # array([[0, 1], [2, 3]])
print(a * 2) # array([[2, 4], [6, 8]])
```

Basic Linear Algebra 線性代數計算

```
import numpy as np
a = np.array([[0,1], [2,3]])
# 轉置矩陣 m*n => n*m
print(a.T) # [[0,2],
           #  [1,3]]
逆矩陣: n*n 矩陣A 存在一個 n*n矩陣B 使得AB = BA = I
inverse = np.linalg.inv(a)
print(inverse)

#內積
print(np.dot(a, inverse))
```

Vector Stacking 堆疊

```
import numpy as np 
a = np.array([[0, 1], [2, 3]])
b = np.array([[4, 5], [6, 7]])
c = np.array([[8, 9], [10, 11]])

# vertical 垂直堆疊
v = np.vstack((a, b, c))
print(v)
[[ 0  1]
 [ 2  3]
 [ 4  5]
 [ 6  7]
 [ 8  9]
 [10 11]]

# horizontal 水平堆疊
h = np.hstack((a, b, c))
print(h)
[[ 0  1  4  5  8  9]
 [ 2  3  6  7 10 11]]
# stack 堆疊
s = np.stack([a, b,c], axis=0)
 print(s)
 [[[ 0  1]
  [ 2  3]]

 [[ 4  5]
  [ 6  7]]

 [[ 8  9]
  [10 11]]]
print(s.shape) #(3, 2, 2)

s = np.stack([a, b,c], axis=1)
[[[ 0  1]
  [ 4  5]
  [ 8  9]]

 [[ 2  3]
  [ 6  7]
  [10 11]]]
print(s.shape) #(2, 3, 2)
```

[更多練習](https://github.com/rougier/numpy-100/blob/master/100_Numpy_exercises.ipynb) **100\_Numpy\_exercises.ipynb**



#### [IntroPandas](https://www.youtube.com/watch?v=RVi3ybwJOEk)

Store Data in DataFrame





