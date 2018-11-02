# 第6课：循环

将以下内容以Jupyter Notebook的方式做练习和自己总结，并保存.ipynb。 

循环：for 和 while

while循环语句
```
>>> i = 0
>>> while i < 6:
...     print(i)
...     i = i + 1
```

break语句
```
>>> i = 0
>>> while i < 6:
...     print(i)
...     i = i + 1
...     if i == 5:
...             break
```

continue语句
```
>>> i = 0
>>> while i < 6:
...     print(i)
...     i = i + 1
...     if i < 5:
...             continue
```

无限循环
```
>>>while True:
	print(‘Hello World!’)
```

for循环和range()函数

可以通过range()函数遍历数字序列
```
>>> for i in range(6):
...     print(i)
```

range()开始、结束、步长
```
>>> for i in range(0, 10, 2):
...     print(i)

>>> for i in range(10, -2, -2):
...     print(i)
```

可以有几种方式：

方式一：for循环
```
>>> sum = 0
>>> for num in range(101):
...     sum = sum + num
...
>>> print(sum)
```

方式二：while循环
```
>>> sum = 0
>>> n = 1
>>> while n < 101:
...     sum = sum + n
...     n+=1
...
>>> print(sum)
```

方式三：导入reduce函数
```
>>> def sum(x, y):
...     return x + y
...
>>> from functools import reduce
>>> print(reduce(sum ,range(1, 101)))
```

扩展练习：
* 1-100的奇数相加之和
* 1-100的偶数相加之和

天气有些热，喝杯冰红茶。

配图来自Twitter：@atikix

![配图6](https://wiki.huihoo.com/images/e/e6/Devopsgirls06.jpg)