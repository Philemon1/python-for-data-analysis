元组


```python
tup=4,5,6
```


```python
tup
```




    (4, 5, 6)




```python
nest_tub=(4,5,6),(7,8)
```


```python
nest_tub
```




    ((4, 5, 6), (7, 8))



用tuple可以将任何数据或迭代器转换为元组


```python
tuple([4,5,6])
```




    (4, 5, 6)




```python
tup=tuple('string')
```


```python
tup
```




    ('s', 't', 'r', 'i', 'n', 'g')




```python
tup[0]
```




    's'



元组中存储的对象可能是可变对象。一旦创建了元组，元组中的对象就不能修改了：


```python
tup=tuple(['foo',[1,2],True])
```


```python
tup[2]
```




    True




```python
tup[2]=False
```


    ---------------------------------------------------------------------------

    TypeError                                 Traceback (most recent call last)

    <ipython-input-12-e84077ea19c6> in <module>
    ----> 1 tup[2]=False
    

    TypeError: 'tuple' object does not support item assignment


如果元组中的某个对象是可变的，比如列表，可以在原位进行修改：


```python
tup[1].append(3)
```


```python
tup
```




    ('foo', [1, 2, 3], True)




```python
(4,None,'foo')+(6,0)+('bar',)
```




    (4, None, 'foo', 6, 0, 'bar')




```python
(4,None,'foo')+(6,0)+('bar')
```


    ---------------------------------------------------------------------------

    TypeError                                 Traceback (most recent call last)

    <ipython-input-16-d93cc779d9b0> in <module>
    ----> 1 (4,None,'foo')+(6,0)+('bar')
    

    TypeError: can only concatenate tuple (not "str") to tuple



```python
(4,None,'foo')+(6,0)+('bar',)
```




    (4, None, 'foo', 6, 0, 'bar')




```python
('fool','bar')*4
```




    ('fool', 'bar', 'fool', 'bar', 'fool', 'bar', 'fool', 'bar')



拆分元组


```python
tup=(4,5,6)
```


```python
a,b,c=tup
```


```python
b
```




    5




```python
 tup = 4, 5, (6, 7)
```


```python
 a, b, (c, d) = tup
```


```python
d
```




    7



但是在Python中，替换可以这样做：


```python
a,b=1,2
```


```python
a
```




    1




```python
b
```




    2




```python
b,a=a,b
```


```python
a
```




    2




```python
b
```




    1



变量拆分常用来迭代元组或列表序列：


```python
seq=[(1,2,3),(3,4,5),(6,7,8)]
```


```python
for a,b,c in seq:
    print(a)
    print(b)
    print(c)
    print('a={0},b={1},c={2}'.format(a,b,c))
```

    1
    2
    3
    a=1,b=2,c=3
    3
    4
    5
    a=3,b=4,c=5
    6
    7
    8
    a=6,b=7,c=8
    

Python最近新增了更多高级的元组拆分功能，允许从元组的开头“摘取”几个元素。它使用了特殊的语法*rest，这也用在函数签名中以抓取任意长度列表的位置参数：


```python
values=1,2,3,4,5,6
```


```python
a,b,*value=values
```


```python
a,b
```




    (1, 2)




```python
value
```




    [3, 4, 5, 6]




```python
a=(1,2,2,1,3,4,5,2)
```


```python
a.count(2)
```




    3



与元组对比,列表的长度可变,内容可变,一般用[],和list函数定义


```python
a_list=[2,3,4,None]
```


```python
a_list
```




    [2, 3, 4, None]




```python
tup=('fool','bar','baz')
```


```python
b_list=list(tup)
```


```python
b_list
```




    ['fool', 'bar', 'baz']




```python
b_list[1]='peakbool'
```


```python
b_list
```




    ['fool', 'peakbool', 'baz']



# 添加和删除元素

可以用append在列表末尾添加元素:


```python
b_list.append('dwarf')
```


```python
b_list
```




    ['fool', 'peakbool', 'baz', 'dwarf']



## insert可以在特定的位置插入元素：


```python
b_list.insert(1,'red')
```


```python
b_list
```




    ['fool', 'red', 'peakbool', 'baz', 'dwarf']



## insert的逆运算是pop，它移除并返回指定位置的元素：


```python
b_list.pop(2)
```




    'peakbool'




```python
b_list
```




    ['fool', 'red', 'baz', 'dwarf']




```python
'dwarf' in b_list
```




    True




```python
"dwarf" not in b_list
```




    False



## 串联和组合列表


```python
[4,None,'foo']+[7,8,(2,3)]
```




    [4, None, 'foo', 7, 8, (2, 3)]




```python
x=[4,None,'foo']
```


```python
x.extend([7,8,(2,3)])
```


```python
x
```




    [4, None, 'foo', 7, 8, (2, 3)]



## 二分搜索和维护已排序的列表


```python
import bisect
```


```python
c = [1, 2, 2, 2, 3, 4, 7]
```


```python
bisect.bisect(c,2)
```




    4




```python
bisect.bisect(c,8)
```




    7




```python
c
```




    [1, 2, 2, 2, 3, 4, 7]




```python
bisect.insort(c,6)
```


```python
c
```




    [1, 2, 2, 2, 3, 4, 6, 7]



注意：bisect模块不会检查列表是否已排好序，进行检查的话会耗费大量计算。因此，对未排序的列表使用bisect不会产生错误，但结果不一定正确。

## 切片


```python
seq=[7,2,3,4,7,5,6,0,7]
```


```python
seq[2:7]
```




    [3, 4, 7, 5, 6]




```python
seq[3:4]=[6,3]
```


```python
seq
```




    [7, 2, 3, 6, 3, 7, 5, 6, 0, 7]




```python
seq[:3]
```




    [7, 2, 3]




```python
seq[-4:]
```




    [5, 6, 0, 7]




```python
seq[-6:-2]
```




    [3, 7, 5, 6]




```python
seq[::2]
```




    [7, 3, 3, 5, 0]




```python
seq[::-1]
```




    [7, 0, 6, 5, 7, 3, 6, 3, 2, 7]



## 清理数据的小栗子


```python
In [171]: states = ['   Alabama ', 'Georgia!', 'Georgia', 'georgia', 'FlOrIda',
   .....:           'south   carolina##', 'West virginia?']

```


```python
import re
def clean_strings(strings):
    result=[]
    for value in strings:
        value=value.strip()
        value=re.sub('[!#?]','',value)
        value=value.title()
        result.append(value)
    return result
```


```python
clean_strings(states)
```




    ['Alabama',
     'Georgia',
     'Georgia',
     'Georgia',
     'Florida',
     'South   Carolina',
     'West Virginia']




```python

```
