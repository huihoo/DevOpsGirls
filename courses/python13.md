# 第13课：函数（Function）

### def
我们来写一个最简单的函数
```
>>> def hello():
...     print ("Hello World!")
...
>>> hello()
Hello World!
```

### lambda
lambda表达式是一行函数，它和普通函数完全一样，它在其它语言中叫匿名函数。

Python使用lambda来创建匿名函数，匿名就是不用像def那样定义函数。

lambda是表达式，它不是代码块。

lambda原型
```
lambda 参数 : 操作(参数)

>>> add = lambda x, y : x + y
>>> print(add(1, 2))
```

写一个简单的Lambda表达式
```
>>> hello = lambda x, y : x*2+y*2
>>> hello(2,3)
10
```

来一个复杂点的：列表排序
```
>>> sl = [(2, 3), (4, 2), (11, -2)]
>>> sl.sort(key=lambda x: x[1])
>>> print(sl)
[(11, -2), (4, 2), (2, 3)]

>>> sl = [(2, 1, 3), (4, 3, 2), (11, 9, -2)]
>>> sl.sort(key=lambda x: x[1])
>>> print(sl)
[(2, 1, 3), (4, 3, 2), (11, 9, -2)]
```

思考下def和lambda有哪些联系和不同？

配图来自Twitter：@neku_draw

![配图13](https://wiki.huihoo.com/images/thumb/7/77/Devopsgirls13.png/717px-Devopsgirls13.png)
