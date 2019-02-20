# 第4课：数据类型（二）

将以下内容以Jupyter Notebook的方式做练习和自己总结，可存档附件到作业后面。 

上节课我们学习了列表[]和元组()，接下来学习集合 {}、字典 {key: value}

### Set & Dict
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

### 数据类
Python 3.7 引入了新的库模块：dataclasses: [PEP 557 -- 数据类](https://docs.python.org/zh-cn/3/whatsnew/3.7.html#whatsnew37-pep557) 大家可了解下。

dataclasses 可简单理解为是一个适合于存储数据对象（data object）或者说数据（data）的 Python 类。

Data Classes can be thought of as "mutable namedtuples with defaults"（数据类可以被认为是“具有默认值的可变命名元组”）大家可思考下？Tuple（元组）是不可变数据类型。

```
>>> from dataclasses import dataclass
>>> @dataclass
... class Point:
...     x: float
...     y: float
...     z: float = 0.0
... 
>>> p = Point(1.5, 2.5)
>>> print(p)
Point(x=1.5, y=2.5, z=0.0)
```

新的 dataclass() 装饰器（decorator）提供了一种声明数据类的方法。数据类使用类变量注释（annotations）来描述其属性。它的构造函数和其他魔法方法（magic methods），如：`__repr__()`、`__eq__()` 和 `__hash__()` 会自动生成。

所谓魔法方法（magic methods）是 Python 的一种高级语法，格式为`__aaa__`，这些方法可以给 Python 类提供特殊功能，如 __init__ 方法可以对实例属性进行初始化。

```
>>> dir(dataclass)
['__annotations__', '__call__', '__class__', '__closure__', '__code__', '__defaults__', '__delattr__', '__dict__', '__dir__', '__doc__', '__eq__', '__format__', '__ge__', '__get__', '__getattribute__', '__globals__', '__gt__', '__hash__', '__init__', '__init_subclass__', '__kwdefaults__', '__le__', '__lt__', '__module__', '__name__', '__ne__', '__new__', '__qualname__', '__reduce__', '__reduce_ex__', '__repr__', '__setattr__', '__sizeof__', '__str__', '__subclasshook__']
```

数据类的扩展阅读：
* [Understanding Python Dataclasses — Part 1](https://medium.com/mindorks/understanding-python-dataclasses-part-1-c3ccd4355c34)
* [Understanding Python Dataclasses — Part 2](https://medium.com/mindorks/understanding-python-dataclasses-part-2-660ecc11c9b8)

好了，我要交作业啦  奖励自己一根雪糕 :)

配图来自Twitter：@makadamixa

![配图4](https://wiki.huihoo.com/images/thumb/9/9a/Devopsgirls04.jpg/1255px-Devopsgirls04.jpg)