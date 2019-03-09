# Python 資料處理及探索分析

影片播放列表: [影片播放列表 ](https://www.youtube.com/playlist?list=PL1f_B9coMEeCqFRgymsH6aZJg-BW_tBWU)

投影片 PDF:[投影片PDF下載連結](https://drive.google.com/file/d/147IuYb3Q5Bea-aZdvyz2aLjpBQ3h6KfO/view)

練習題下載：[連習題下載](https://drive.google.com/file/d/1U3Xj2V2FekxqGetDGjDNvatKFYvu5z9k/view)

#### [Python\_Numpy](https://www.youtube.com/watch?v=GxdDFtz9KrM)

安裝：

```
pip install numpy
```

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

安裝

```
pip install pandas
```

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

請參考[100-pandas-puzzles](https://github.com/ajcr/100-pandas-puzzles/blob/master/100-pandas-puzzles.ipynb)做更多 pandas 的資料操作練習

#### [PandasExercise](https://www.youtube.com/watch?v=eItz2E4WmVM)

安裝

```
pip install matplotlib
pip install sklearn
```

[The iris data set 鳶尾花卉數據集](https://zh.wikipedia.org/wiki/安德森鸢尾花卉数据集)（英文：_Iris \_flower \_data set_）

它最初是埃德加·安德森從加拿大加斯帕半島上的鳶尾屬花朵中提取的形態學變異數據，後由羅納德·費雪作為判別分析的一個例子，運用到統計學中。

其數據集包含了150個樣本，都屬於鳶尾屬下的三個亞屬，分別是山鳶尾、變色鳶尾和維吉尼亞鳶尾。四個特徵被用作樣本的定量分析，它們分別是花萼和花瓣的長度和寬度。基於這四個特徵的集合，費雪發展了一個線性判別分析以確定其屬種。

150 observation 樣本

3 species 種類 : 山鳶尾, 變色鳶尾, 維吉尼亞鳶尾

4 features 特徵

* sepal length  花萼長度
* sepal width  花萼寬度
* petal length 花瓣長度
* peta width 花瓣寬度

Load Dataset

```
import matplotlib.pyplot as plt
import numpy as np
from sklearn import datasets
import pandas as pdi
# 載入 iris data set
iris = datasets.load_iris() 

type(iris.data)
# numpy.ndarray

iris.feature_names
#['sepal length (cm)',
# 'sepal width (cm)',
# 'petal length (cm)',
# 'petal width (cm)']
```

referance [https://scikit-learn.org/stable/datasets/index.html](https://scikit-learn.org/stable/datasets/index.html)

Make a DataFrame

```
# Make a DF
iris_DF = pd.DataFrame(iris.data, columns= iris.feature_names)
iris_DF.head()

# 增加一個 species 欄位，值為 temp
iris_DF["species"] = "temp"

# 第 0~49 行的 species 的值改為 setosa
iris_DF.loc[:49,'species'] = "setosa"

# 第 50~99 行的 species 的值改為 versicolor
iris_DF.loc[50:99,'species'] = "versicolor"

# 第 100~149 行的 species 的值改為 virginica
iris_DF.loc[100:149,'species'] = "virginica"
iris_DF

# group species 並顯示大小
iris_DF.groupby("species").size()
#species
#setosa        50
#versicolor    50
#virginica     50
#dtype: int64

# 查看 species 的描述，顯示基礎統計資料
iris_DF['species'].describe()
#count        150
#unique         3
#top       setosa
#freq          50
#Name: species, dtype: object
```

EDA

```
# 依據第一列 產生一個 box plot 
iris_DF.iloc[:,1].plot(kind = "box")

# Show the plot
plt.show()
```

[pandas.DataFrame.plot 參考](https://pandas.pydata.org/pandas-docs/stable/reference/api/pandas.DataFrame.plot.html)

```
kind : str
'line' : line plot (default)
'bar' : vertical bar plot
'barh' : horizontal bar plot
'hist' : histogram
'box' : boxplot
'kde' : Kernel Density Estimation plot
'density' : same as 'kde'
'area' : area plot
'pie' : pie plot
'scatter' : scatter plot
'hexbin' : hexbin plot
```

[箱形圖（英文：_Box plot_）](https://zh.wikipedia.org/wiki/箱形圖)，又稱為盒鬚圖，是一種用作顯示一組數據分散情況資料的統計圖，它能顯示出一組數據的最大值、最小值、中位數、及上下四分位數

```
                        +-----+-+       
```

\*           o     \|-------\|   + \| \|---\|

```
                        +-----+-+    
```

+---+---+---+---+---+---+---+---+---+---+   分数

0   1   2   3   4   5   6   7   8   9  10

這組數據顯示出：

最小值\(minimum\)=5

下四分位數\(Q1\)=7

中位數\(Med --也就是Q2\)=8.5

上四分位數\(Q3\)=9

最大值\(maximum \)=10

平均值=8

四分位間距\(interquartile range\)= {\displaystyle \(Q3-Q1\)} {\displaystyle \(Q3-Q1\)}=2 \(即ΔQ\)

在區間 Q3+1.5ΔQ, Q1-1.5ΔQ 之外的值被視為應忽略\(farout\)。

* farout: 在圖上不予顯示，僅標註一個符號∇。

* 最大值區間： Q3+1.5ΔQ

* 最小值區間： Q1-1.5ΔQ

最大值與最小值產生於這個區間。區間外的值被視為outlier顯示在圖上.

* mild outlier （離群值\) = 3.5
* extreme outlier \(極端值\) = 0.5

Box Plot 箱行圖

```
## 做quantile的EDA

# Print the 5th and 95th percentiles
# 所有欄位(sepal length, sepal width, peta length, peta width)
kind = iris_DF.columns  
# 百分位數  
q = [0.05,0.25,0.75, 0.95]
print(iris_DF[kind].count())
print(iris_DF[kind].quantile(q))

# # Generate a box plot
iris_DF[kind].plot(kind='box') #draw all the column
plt.show()
```

Scatter Plot 散布圖 or 散點圖

```
iris_DF.plot(x = "petal length (cm)", y = "petal width (cm)", kind = "scatter")
iris_DF.plot(x = "petal length (cm)", y = "sepal length (cm)", kind = "scatter", logx= True)
plt.show()
```

Pandas plot API

* Three different DataFrame plot idioms

  * iris.plot\(kind='hist'\)

  * iris.plt.hist\(\)

  * iris.hist\(\)

* Syntax/result differ!

* Plandas API still evolving: check documentation!

Draw a histogram\(長條圖\)

Visual EDA: all data

```
#Filtering by species

indices = iris_DF['species'] == 'setosa'
setosa = iris_DF.loc[indices,:] # extract new DataFrame
indices = iris_DF['species'] == 'versicolor'
versicolor = iris_DF.loc[indices,:] # extract new DataFrame
indices = iris_DF['species'] == 'virginica'
virginica = iris_DF.loc[indices,:] # extract new DataFrame

## all flowers 
iris_DF.plot(kind= 'hist', bins=50, range=(0,8), alpha=0.3, edgecolor='black')
plt.title('Entire iris data set')
plt.xlabel('[cm]')
plt.figure(figsize=(18, 12), dpi=600)
plt.show()

# visualize setosa data
setosa.plot(kind = "hist", bins = 50, range = (0,8), alpha = 0.3, edgecolor = "black")
plt.title("setosa data set")
plt.xlabel("[cm]")
plt.show()
```

#### [PandasExercise2](https://www.youtube.com/watch?v=bYTxKNJ10gw)

更多 Panda 練習

[pandas\_exercise](https://github.com/guipsamora/pandas_exercises)

[kaggle learn](https://www.kaggle.com/learn/pandas)



#### [IntroMatplotlib](https://www.youtube.com/watch?time_continue=7&v=HLSJkoTH7Us)

Matplotlib 畫圖library

```
import matplotlib.pyplot as plt
# 在 jupyter notebook 畫圖
%matplotlib inline
```

Plotting

```
import matplotlib.pyplot as plt
%matplotlib inline
import pandas as pd

# 畫出一個 sin 圖形
import numpy as np
x = np.arange(0, 3 * np.pi, 0.1)
y = np.sin(x)
print(x)
print(y)
plt.plot(x, y)
plt.show()
```

雙圖合併

```
x = np.arange(0, 3 * np.pi, 0.1)
y_sin = np.sin(x)
y_cos = np.cos(x)

# 第一張 sin 圖
plt.plot(x, y_sin)

# 第二張 cos 圖
plt.plot(x, y_cos)

# 設定 x 軸 名稱
plt.xlabel("x axis label")

# 設定 y 軸 名稱
plt.ylabel("y axis label")

# 設定 圖片標題 名稱
plt.title("Since and Cosine")

# 設定 解說
plt.legend(["Sine", "Cosine"])

# 顯示圖片
plt.show()
```

使用 Object 方法畫圖

```
fig = plt.figure()
#新增Figure的軸（左,下,寬度,高度)，範圍佔Figure的比例（數值介於0-1）
axes = fig.add_axes([0.1, 0.1, 0.8, 0.8])
axes.plot(x,y_sin)
axes.plot(x,y_cos)
# 注意這邊不一樣 object 使用 set_xlable 和 set_ylabel
axes.set_xlabel("x axis label")
axes.set_ylabel("y axis label")
axes.set_title("Sine and Cosine")
plt.legend(["Sine", "Cosine"])
```





