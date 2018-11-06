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
Python使用lambda来创建匿名函数，匿名就是不用像def那样定义函数。lambda是表达式，不是代码块。

写一个简单的Lambda表达式
```
>>> hello = lambda x, y : x*2+y*2
>>> hello(2,3)
10
```

思考下def和lambda有哪些联系和不同？


