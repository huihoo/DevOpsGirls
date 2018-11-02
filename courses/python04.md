# 第4课：数据类型（二）

将以下内容以Jupyter Notebook的方式做练习和自己总结，可存档附件到作业后面。 

上节课我们学习了列表[]和元组()，接下来学习集合 {}、字典 {key: value}

集合（set）是一个无序不重复元素的序列，如：
```
>>>set1 = set() # 空集合用set() 
>>>set2 = {'a', 'b', 'c', 'd'} 
>>>set2.add(“e”)
```

字典可存储任意类型对象，列表是有序的对象集合，字典是无序的对象集合。
```
>>> dict1 = {'Name': 'Allen', 'Age': 44}
>>> dict1['Age'] = 34
```

接着，我们展开这些内容。

集合操作：添加元素、移除元素、集合个数、是否存在、清空集合

1、添加元素
```
>>>set2.add(‘f’) 或 set2.update(‘f’) # 注意：无序
```

2、移除元素
```
>>>set2.remove(‘f’) 或 set2.discard('f') 或 set2.pop()
```

3、集合个数
```
>>>len(set2)
```

4、是否存在
```
>>>'a' in set2
```

5、清空集合
```
>>>set2.clear()
```

字典操作：访问、修改、个数、删除

1、访问
```
>>> dict1['Name']
```

2、修改
```
>>> dict1['Name'] = "Python"
```

4、个数
```
>>> len(dict1)
```

4、删除
```
>>> del dict1['Name'] # 删除键
>>> dict1.clear() # 清空字典，空字典还在
>>> del dict1 # 删除字典，没了
```

还有些其它字典内置函数&方法，自己可找找学习下。

最后，做一个循环输出字典键或字典值的练习，提示：for循环、keys、values。

```
>>> dict = {1: "C", 2: "C++", 3: "Java", 4: "Python"}
```

我要交作业啦  奖励自己一根雪糕 :)

配图来自Twitter：@makadamixa

![配图4](https://wiki.huihoo.com/images/thumb/9/9a/Devopsgirls04.jpg/1255px-Devopsgirls04.jpg)