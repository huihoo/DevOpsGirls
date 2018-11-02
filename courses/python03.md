# 第3课：数据类型（一）

将以下内容以Jupyter Notebook的方式做练习和自己总结，可存档附件到作业后面。 

Python3 的六个标准数据类型中：
* 不可变数据（3个）：Number（数字）、String（字符串）、Tuple（元组）；
* 可变数据（3个）：List（列表）、Dictionary（字典）、Set（集合）。

ps：集合有可变集合(set())和不可变集合(frozenset)两种。

接下来我们分两次课介绍列表、元组、集合和字典

列表 []、元组 ()、集合 {}、字典 {key: value}

首先了解下Number：整数(int)、浮点数(float)、复数(complex)

也可以使用十六进制和八进制来代表整数

```
>>> number = 0xB0F # 十六进制
>>> number
2831
>>> number=0o27 # 八进制
>>> number
23
```
类型转换

如：浮点数转整数
```
>>> a = 3.3
>>> int(a)
3
```
内置的数学函数、随机数函数、三角函数、数学常量

依此举例：
```
>>>abs(-3)
>>>import random
>>>random.randint(1,99)
57

>>> math.sin(100)
-0.5063656411097588

>>> math.pi
3.141592653589793

>>> math.e
2.718281828459045
```

大家去去找到这些内容完整介绍，并试试其它一些函数。

Python3的列表和元组很类似，区别是元组的元素不可变。

列表用[]，元组用()，如：
```
>>>list1 = [1, 2, 3, 4, 5]
>>>list1[0] = 10 # 合法
>>>tup1 = (1, 2, 3, 4, 5)
>>>tup1[0] = 10 # 非法
```

配图来自：Twitter

![配图03](https://wiki.huihoo.com/images/thumb/b/b9/Devopsgirls03.jpg/1280px-Devopsgirls03.jpg)