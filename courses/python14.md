# 第14课：面向对象（Object orientation）（一）

Python设计之初就是一门面向对象编程语言。对象是Python最核心的概念，在Python的世界里，一切都是对象，一个整数是对象，一个字符串是对象，一个字典是对象。

在Python中，已预先定义了一些常见类型对象，如：int类型、str类型、list类型等。这些类型对象通过实例化，可以创建相应的实例对象，如：int对象、str对象、list对象等。
```
>>> help(int)
class int(object)
 |  int(x=0) -> integer
 |  int(x, base=10) -> integer
>>> help(str)
class str(object)
 |  str(object='') -> str
 |  str(bytes_or_buffer[, encoding[, errors]]) -> str
>>> help(list)
class list(object)
 |  list() -> new empty list
 |  list(iterable) -> new list initialized from iterable's items
```

此外，Python也允许通过class a(object)这样的表达式定义自己的类型对象。

Python的对象系统庞大而复杂，核心使用C语言实现。

PS：Python语言核心：类型系统、对象系统。这也几乎是所有OO语言的核心，也是构建大规模Python应用的基础，所以掌握类型系统和对象系统是学习掌握一门新语言的关键。

### 一些面向对象概念
* 类(class)
* 实例化(instantiation)
* 方法(method)
* 对象(object)
* 数据成员(data member)
* 类变量(class variables)
* 实例变量(instance variable)
* 继承(inheritance)：基类(base class)、派生类(derived class)
* 方法重写(override)


