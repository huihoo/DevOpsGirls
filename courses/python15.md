# 第15课：面向对象（Object orientation）（二）

### 继承

### 方法重载

### 运算符重载

### 类的专有方法

### 自省
对人来讲，自省（introspection）就是对自身思想、情绪、动机和行为的审视，能帮助我们更好的认识和改善自己。同理，Python自省能帮助开发者更深入了解和洞察Python对象所包含或隐藏的各种细节。

Python包含了很多内置函数和模块可帮助到我们。

#### dir函数
dir是用于自省一个重要的函数，它返回一个对象所拥有的属性和方法。
```
当前作用域
>>> dir()
['__annotations__', '__builtins__', '__doc__', '__loader__', '__name__', '__package__', '__spec__', 'add', 'keyword', 'sl', 'sys']

之前第13课定义的sl
>>> dir(sl)
['__add__', '__class__', '__contains__', '__delattr__', '__delitem__', '__dir__', '__doc__', '__eq__', '__format__', '__ge__', 
...
```

#### sys模块
sys模块的属性
```
>>> import sys
>>> dir(sys)
['__displayhook__', '__doc__', '__excepthook__', '__interactivehook__', '__loader__', '__name__', '__package__', '__spec__', '__stderr__', 
...
```

#### keyword模块
keyword模块的关键字列表
```
>>> import keyword
>>> keyword.kwlist
['False', 'None', 'True', 'and', 'as', 'assert', 'break', 'class', 'continue', 'def', 'del', 'elif', 'else', 'except', 'finally', 'for', 'from', 'global', 'if', 'import', 'in', 'is', 'lambda', 'nonlocal', 'not', 'or', 'pass', 'raise', 'return', 'try', 'while', 'with', 'yield']
```

keyword模块的属性
```
>>> import keyword
>>> dir(keyword)
['__all__', '__builtins__', '__cached__', '__doc__', '__file__', '__loader__', '__name__', '__package__', '__spec__', 'iskeyword', 'kwlist', 'main']
```

#### inspect模块
```
>>> import inspect
>>> print(inspect.getmembers(sl))
>>> print(inspect.getmembers(str))
```

#### type和id
type()和id()返回对象类型和对象id
```
>>> print(type(sl))
<class 'list'>
>>> print(type(9))
<class 'int'>
>>> name = "python"
>>> print(id(name))
4552783720
```

配图来自Twitter：@chengr28

![配图15](https://wiki.huihoo.com/images/a/a0/Devopsgirls15.jpg)
