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

```
import pandas as pd
df = pd.DataFrame({
  'names': ['Bob', 'Jessica', 'Mary', 'John', 'Mel'], 
  'births': [968,155,77,578,973]
})

# 從list
names = ['Bob', 'Jessica', 'Mary', 'John', 'Mel', 'Jim']
births = [968, 155, 77, 578, 973, 968 ]
data = list(zip(names, births))
data_df = pd.DataFrame(data, columns=['Names', 'Births'])
```

Work With CSV

* header
* row index
* encoding

匯入資料

```
import pandas as pd
df = pd.read_csv('birth_data.csv')
# 指定欄位名稱
df = pd.read_csv('birth_data.csv', names=['births', 'names'])
# 指定第一行為 coloum index
df = pd.read_csv('birth_data.csv', index_col=0)
```

匯出資料

```
import pands as pd
# 儲存在目前的目錄
df.to_csv('birth_data.csv') # index=True/False
```

切分資料

```
df.head(n=5) # 前面幾筆
df.tail(n=5) # 後面幾筆
df[1:5] # 1 to 4 資料
df.sample(5) # 隨機n筆資料
```

Make a Dataset

```
# Function to generate test data
def CreateDataSet(Number=1):
    Output = []
    for i in range(Number):
        # Create a weekly (mondays) date range
        rng = pd.date_range(start='1/1/2009', end='12/31/2012', freq='W-MON') #random number generator

        # Create random data
        data = np.random.randint(low=25, high=1000, size=len(rng))

        # Status pool
        status = [1,2,3]

        # Make a random list of statuses
        random_status = [status[np.random.randint(low=0, high=len(status))] for i in range(len(rng))]

        # State pool
        states = ['GA','FL','fl','NY','NJ','TX']

        # Make a random list of states 
        random_states = [states[np.random.randint(low=0, high=len(states))] for i in range(len(rng))]

        Output.extend(zip(random_states, random_status, data, rng))
        #extend& append 差異

    return Output

dataset = CreateDataSet(4)
dataset
len(dataset) #check shape
df = pd.DataFrame(data=dataset, columns=['State','Status','CustomerCount','StatusDate'])
df.head(10)
```

Data Observation 資料觀察

```
df['State'].unique() # 在State欄位有幾個唯一質
#array(['FL', 'TX', 'GA', 'fl', 'NY', 'NJ'], dtype=object)

df['State'].value_counts() # 在State每一個數值計算字數
#GA    155
#NJ    148
#FL    135
#fl    135
#TX    132
#NY    131
#Name: State, dtype: int64

df["StatusDate"].unique().shape
#(209,)

df.info # 讀取資料表的狀態
#<class 'pandas.core.frame.DataFrame'>
#RangeIndex: 836 entries, 0 to 835
#Data columns (total 4 columns):
#State            836 non-null object
#Status           836 non-null int64
#CustomerCount    836 non-null int64
#StatusDate       836 non-null datetime64[ns]
#dtypes: datetime64[ns](1), int64(2), object(1)
#memory usage: 26.2+ KB

df.columns
#Index(['State', 'Status', 'CustomerCount', 'StatusDate'], dtype='object')

```

Index and Select Data

* Square brackets
* Advanced methods
* loc
* iloc

Column Access

```
print(df["CustomerCount"].head(5))
print(type(df["CustomerCount"]))
#0    506
#1    979
#2    118
#3    302
#4    257
#Name: CustomerCount, dtype: int64
#<class 'pandas.core.series.Series'>

print(df[["CustomerCount"]].head(5))
print(type(df[["CustomerCount"]]))
#   CustomerCount
#0            506
#1            979
#2            118
#3            302
#4            257
#<class 'pandas.core.frame.DataFrame'>
```





















