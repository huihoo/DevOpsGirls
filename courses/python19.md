# 第19课：闭包（Closures）

### 什么是闭包
维基百科介绍

在计算机科学中，闭包（英语：Closure），又称词法闭包（Lexical Closure）或函数闭包（function closures），是引用了自由变量的函数。这个被引用的自由变量将和这个函数一同存在，即使已经离开了创造它的环境也不例外。所以，有另一种说法认为闭包是由函数和与其相关的引用环境组合而成的实体。闭包在运行时可以有多个实例，不同的引用环境和相同的函数组合可以产生不同的实例。

闭包，就好比一个封闭的包裹，里面包裹着自由变量，哪里可以访问到这个包裹，哪里就可以访问到这个自由变量。

### 为什么要使用闭包
闭包避免了全局变量的使用，闭包允许将函数与其所操作的相关数据和环境关连起来。

### 如何使用闭包
一个闭包就是你调用了一个函数A，这个函数A返回了一个函数B给你。这个返回的函数B就叫做闭包，你在调用函数A的时候传递的参数就是自由变量。
```
>>> def func(name):
...     def inner_func(age):
...         print ('name:', name, 'age:', age)
...     return inner_func
... 
>>> hello = func('huihoo')
>>> hello(18) 
name: huihoo age: 18
```

调用func的时候就产生了一个闭包inner_func，该闭包也包含name自由变量。当func生命周期结束了，name自由变量依然存在，因为它被闭包引用，所以不会被回收。

配图来自Twitter：@MacciattoS2

![配图19](https://wiki.huihoo.com/images/a/af/Devopsgirls19.jpg)
