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

# 如果要取兩行，只能用DataFrame
print(df[["CustomerCount", "Status"]].head(5))
#   CustomerCount  Status
#0            506       2
#1            979       2
#2            118       2
#3            302       1
#4            257       1

# slicing 取出StatusDate第100筆至105筆的資料
print(df[100:106])
```

Slicing with Pandas

* DataFrame.loc \(label-base\)
* DataFrame.iloc \(integer position-base\)

loc

```
# row 依據 row 取資料
print(df.loc[0:3])
#  State  Status  CustomerCount StatusDate
#0    FL       2            506 2009-01-05
#1    TX       2            979 2009-01-12
#2    GA       2            118 2009-01-19
#3    fl       1            302 2009-01-26

# column 依據 column 取資料
print(df.loc[:,["State", "Status"]].head())
#State Status
#0 FL 2
#1 TX 2
#2 GA 2
#3 fl 1
#4 FL 1

#Slicing on both row & column
print(df.loc[0:5,"State"])
#0    FL
#1    TX
#2    GA
#3    fl
#4    FL
#5    GA
#Name: State, dtype: object
```

iloc

```
# row 依據 row 取資料
print(df.iloc[0:3])
#  State  Status  CustomerCount StatusDate
#0    FL       2            506 2009-01-05
#1    TX       2            979 2009-01-12
#2    GA       2            118 2009-01-19


# column 依據 column 取資料
print(df.iloc[:,2.head())
#0    506
#1    979
#2    118
#3    302
#4    257
#Name: CustomerCount, dtype: int64

#Slicing on both row & column
print(df.iloc[1:5,[2,3]])
#   CustomerCount StatusDate
#1            979 2009-01-12
#2            118 2009-01-19
#3            302 2009-01-26
#4            257 2009-02-02
```

Conditional Data

```
# 取得 State 欄位 等於 'FL' 的資料
df.loc[df.State == 'FL']
# 取得 State 欄位 等於 'FL' 和 Status == 3 的資料
df.loc[(df.State == 'FL') & (df['Status'] == 3)]
# 取出並+1
print((df['Status'] + 1).head())
# 取出 Status 的值
print(df['Status'].head().values)
```

Generate a vector by function

```
# 套用 func 到每個 Column，每個column有幾個row
print(df.apply(len, axis=0)) # 0 -> column
# 套用 func 到每個 row，每個row有幾個column
print(df.apply(len, axis=1)) # 1 -> row

# 計算Status數值並回傳Text
def text(df):
    status = df['Status']
    return 'correct' if status == 1 else 'error'

# 對每一個 row 作運算，計算完結果存在StatusText 欄位
df['StatusText'] = df.apply(text, axis=1) 
df.head()
#State Status  CustomerCount StatusDate  StatusText
#0 FL  2 506 2009-01-05  error
#1 TX  2 979 2009-01-12  error
#2 GA  2 118 2009-01-19  error
#3 fl  1 302 2009-01-26  correct
#4 FL  1 257 2009-02-02  correct
```

Get the Summary Data by group

```
# group by State
g_state = df.groupby(['State'])
# 顯示 g_state 的大小
g_state.size()
#State
#FL    135
#GA    155
#NJ    148
#NY    131
#TX    132
#fl    135
#dtype: int64

# 取得 group 好的 NJ 資料
g_state.get_group("NJ").head()
#17  NJ  3 607 2009-05-04  error
#34  NJ  2 45  2009-08-31  error
#46  NJ  3 490 2009-11-23  error
#47  NJ  2 689 2009-11-30  error
#50  NJ  2 232 2009-12-21  error

# 匯總
g_state.sum()

# 計數
g_state.count()

# 計算
g_state.sum()/g_state.count()
```

Group by multiple indexes and hierarchical

```
# Group 兩個以上欄位
g_state = df.groupby(['StatusDate','State'], axis=0, sort=True).sum()
g_state.head(10)
```

Comine DataFrame

* LFFT join
* IGHT join 
* OUTER join 交集 
* INNER join 聯集

```
# 欄位一樣只接使用 concat
df.concat([df1, df2])

df1 = pd.DataFrame({'A': ['A0', 'A1', 'A2', 'A3'],
                    'B': ['B0', 'B1', 'B2', 'B3'],
                    'C': ['C0', 'C1', 'C2', 'C3'],
                    'D': ['D0', 'D1', 'D2', 'D3']},
                    index=[0, 1, 2, 3])


df2 = pd.DataFrame({'A': ['A4', 'A5', 'A6', 'A7'],
                    'B': ['B4', 'B5', 'B6', 'B7'],
                    'C': ['C4', 'C5', 'C6', 'C7'],
                    'D': ['D4', 'D5', 'D6', 'D7']},
                    index=[4, 5, 6, 7])
## 垂直接上 dataframe
result = pd.concat([df1, df2], axis = 0) #default = 0


## 水平接上 dataframe
result = pd.concat([df1, df2], axis = 1)


# join 有left表和 right 表，關聯欄位 key1 和 key2，已left表為主(會有NaN問題)
pd.merge(left,right, on=['key1', key2], how=left)
# Join
left = pd.DataFrame({'key': ['K0', 'K1', 'K2', 'K3'],
                      'A': ['A0', 'A1', 'A2', 'A3'],
                      'B': ['B0', 'B1', 'B2', 'B3']})

right = pd.DataFrame({'key': ['K0', 'K1', 'K2', 'K3'],
                       'C': ['C0', 'C1', 'C2', 'C3'],
                       'D': ['D0', 'D1', 'D2', 'D3']})

result = pd.merge(left, right, on = 'key')


# 
left = pd.DataFrame({'key1': ['K0', 'K0', 'K1', 'K2'],
                      'key2': ['K0', 'K1', 'K0', 'K1'],
                      'A': ['A0', 'A1', 'A2', 'A3'],
                      'B': ['B0', 'B1', 'B2', 'B3']})

right = pd.DataFrame({'key1': ['K0', 'K1', 'K1', 'K2'],
                       'key2': ['K0', 'K0', 'K0', 'K0'],
                       'C': ['C0', 'C1', 'C2', 'C3'],
                       'D': ['D0', 'D1', 'D2', 'D3']})

# left join
result = pd.merge(left, right, on=['key1', 'key2'], how='left')

# right join
result = pd.merge(left, right, how='right', on=['key1', 'key2'])

# outer join
result = pd.merge(left, right, how='outer', on=['key1', 'key2'])

# inner join
result = pd.merge(left, right, how='inner', on=['key1', 'key2'])
```

接下來的練習題，皆可從以下的資源找到答案。

* [10 minutes to pandas](http://pandas.pydata.org/pandas-docs/stable/10min.html)

* [pandas basics ](http://pandas.pydata.org/pandas-docs/stable/basics.html)

* [tutorials ](http://pandas.pydata.org/pandas-docs/stable/tutorials.html)

* [cookbook and idioms ](http://pandas.pydata.org/pandas-docs/version/0.17.0/cookbook.html#cookbook)

* [Guilherme Samora's pandas exercises](https://github.com/guipsamora/pandas_exercises)



### 請參考[100-pandas-puzzles](https://github.com/ajcr/100-pandas-puzzles/blob/master/100-pandas-puzzles.ipynb)做更多 pandas 的資料操作練習 {#%E8%AB%8B%E5%8F%83%E8%80%83-%3Ca-href%3D%22https%3A%2F%2Fgithub.com%2Fajcr%2F100-pandas-puzzles%2Fblob%2Fmaster%2F100-pandas-puzzles.ipynb%22-rel%3D%22nofollow%22-target%3D%22_blank%22%3E100-pandas-puzzles%3C%2Fa%3E-%E5%81%9A%E6%9B%B4%E5%A4%9A-pandas--%E7%9A%84%E8%B3%87%E6%96%99%E6%93%8D%E4%BD%9C%E7%B7%B4%E7%BF%92}



