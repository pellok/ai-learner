# Python 資料處理及探索分析

資料與程式碼: [程式碼與練習題解答 ](https://doc-10-a8-docs.googleusercontent.com/docs/securesc/0e6o73khf30bge47v75ur1f0ansg0qb7/hbkigjjjm9spdhr1qgp49psdmg87eo5h/1551852000000/17581372301209011741/15400212421688111872/1xiJegBUNO6vIwDKleslxamYABYGO_DaE?e=download&nonce=bdftdsv7idrii&user=15400212421688111872&hash=21v2ojv6o7dsjb7o42etsnqkmoobfdre)

影片播放列表:[ 影片播放列表 ](https://www.youtube.com/playlist?list=PL1f_B9coMEeCcmGIoOvHXPhKepnS6lM8P)

投影片 PDF:[投影片PDF下載連結](https://drive.google.com/file/d/1Tn_swvB0JxeIDhyrJmbZdwvNsV8_-Rga/view)

#### [part4\_Function](https://www.youtube.com/watch?v=h9EgCu0FusA)

Syntax, Define, Call Function, Repetition, Return Statement, Multiple return values,

Anonymous Function - Lambda

Map Function

Global, Local variables

#### [part5\_Generators](https://www.youtube.com/watch?time_continue=2&v=5MmlPvbXpKA)

generator with for loop

yield: 保留function 狀態，等待下次呼叫

```
def generator_example():
    a=1
    yield print(a) #1
    a+=1
    yield print(a) #2
    return

for i in generator_example():
    continue
```

```
def generator_example():
  yield print(1)
  yield print(2)

gen = generator_example()
try :
  gen.__next__()
  gen.__next__()
  gen.__next__()
except StopIteration:
  pass
```

好處：

Memory Usage - by using list 驗證

Module

re , os , psutil

#### [part6\_Regular\_Expression](https://www.youtube.com/watch?v=8MLJqa2metc)

Regular Expression 正規表示式

[更詳盡的 regular expression 符號解釋](/ https://atedev.wordpress.com/2007/11/23/正規表示式-regular-expression/)

[常見的 regular expression 寫法](https://www.analyticsvidhya.com/blog/2017/03/extracting-information-from-reports-using-regular-expressons-library-in-python/)

special characters

| 符號 | 說明 |
| :--- | :--- |
| . | 任何字元 |
| \* | 匹配零個或重複字元 |
| + | 匹配一個或重複字元 |
| {m} | 匹配m次重複字元 |
| {m,n} | 匹配m~n次 |
| \ | 跳脫字元 |
| \[\] \[0-9\] \[a-z\] | 中括號裡面所有字元都是想匹配的 |

比對Email

import re

re.findall\("\(\[A-Za-z0-9.\_\]+@\[A-Za-z.\]+\[com\|edu\].tw\)"\)

\#Output: \['felix2018@iis.sinica.edu.tw'\]



#### [part7\_python](https://www.youtube.com/watch?v=iahoJKy4poI)

Class, init , self, object

[更多練習](https://www.w3resource.com/python-exercises/)



