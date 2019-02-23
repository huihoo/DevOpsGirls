# 第15课：面向对象（Object orientation）（二）

### 继承
若没有继承，它也不能称为"类"。想想父类、子类，父母、儿女。

在面向对象编程中，类通过从其它类继承属性、方法，这样就形成了一个“家族”，整个“家族”里的每个类共享相同的属性和方法。而每次向“家族”增加新成员时也不必从头开始。

### 方法重载
Python 的方法重载或者函数重载这块，一直都存在一些争议。对于 C++ 这类静态语言，函数重载很自然、也很推崇。   

如 C++ 中，函数 EatApple、EatOrange、EatBanana 可以用同一个函数名 Eat 表示，而用不同的类型参数加以区别：
```
void EatApple(...); 可改为 void Eat(Apple ...);
void EatOrange(...); 可改为 void Eat(Orange ...);
void EatBanana(...); 可改为 void Eat(Banana ...);
```
这样，函数名被重载，便于记忆，也提高了函数的易用性。

而 Python 这类动态语言，是否需要重载，大家各执己见。有兴趣的同学可参考知乎上的讨论：[为什么 Python 不支持函数重载？其他函数大部分都支持的？](https://www.zhihu.com/question/20053359) 并自己展开。

另外，Python 中的函数（function）和方法（method）是有一定区别的，简单记忆，方法随类而出现。
* 与类和实例无绑定（unbound）关系的 def 属于函数（function），是在 class 外部定义的函数。
* 与类和实例有绑定关系（bound）的 def 属于方法（method），是在 class 内部定义的函数。

### 类专有方法
Python 有很多类似 `__init__` 、`__del__ `、` __add__`、` __sub__` 这样的特殊方法（也叫魔法方法），如：

* `__init__` : 构造函数，对象创建时调用
* `__del__` : 析构函数，对象收回时调用
* `__add__`: 加运算
* `__sub__`: 减运算
* `__mul__`: 乘运算
* `__div__`: 除运算
* `__mod__`: 取余运算
* `__pow__`: 乘方
* `__or__`：或运算
* `__repr__`/`__str__` : 打印，转换
* `__call__`：函数调用
* `__getattr__`：属性引用
* `__setattr__`：属性赋值
* `__getitem__`: 索引运算
* `__setitem__` : 索引赋值
* `__len__`: 长度
* `__cmp__`: 比较运算

### 运算符重载
对已有的运算符进行重新定义，实现新的功能。

如：构造函数和析构函数：`__init__` 、`__del__ `

它们的主要作用是对象的创建和回收，当实例创建时，就会调用__init__构造方法。当实例对象收回时，析构函数__del__会被执行。

```
>>> class Person():
...     def __init__(self, n):
...             self.name = n
...             print("__init__", self.name)
...     def __del__(self):
...             print("__del__")
... 
>>> p = Person('Allen')
__init__ Allen
>>> p = 'Peter'
__del__
```

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
