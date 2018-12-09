# 第14课：面向对象（Object orientation）（一）

Python设计之初就是一门面向对象编程语言。对象是Python最核心的概念，在Python的世界里，一切都是对象，一个整数是对象，一个字符串是对象，一个字典是对象。

在Python中，已预先定义了一些常见类型对象，如：int类型、str类型、list类型等。这些类型对象通过实例化，可以创建相应的实例对象，如：int对象、str对象、list对象等。

对象 = 属性（attribute） + 方法（method）

如：球（ball）

属性有：
* ball.color
* ball.size

方法有：
* ball.kick()
* ball.throw()

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
* 类（class）
具有相同属性和方法的对象的集合。
* 对象（object）
对象是类的实例。
* 属性（attribute）
属性并不属于类，它属于各个实例。属性引用：obj.name
* 方法（method）
类中定义的函数。
* 实例化（instantiation）
创建类的具体对象。
* 数据成员（data member）
类变量或者实例变量。
* 类变量（class variable）
类变量定义在类中且在函数体之外，在整个实例化的对象中是公用的。
* 实例变量（instance variable）
定义在方法中的变量，只作用于当前实例的类。
* 继承（inheritance）：基类（base class）、派生类（derived class）
* 多态（polymorphism）
同一个方法，不同的行为。不同的类可以有同名的两个或多个方法。
* 方法重载（override）
若从父类继承的方法不能满足子类的需求，可以对其进行改写（重写）.

### 公共私有
* 公共方法
* 私有方法
__private_method：两个下划线开头，只能在类的内部调用。self.__private_methods
* 公共属性
* 私有属性 
__private_attrs：两个下划线开头，只能在类内部的方法中使用。self.__private_attrs

### 创建类
```
>>> class Ball:
...      def bounce(self):
...          if self.direction == "down":
...              self.direction = "up"
...
>>>
```
### 实例化
```
创建类的一个实例，并设置一些属性
>>> myBall = Ball()
>>> myBall.direction = "down"
>>> myBall.color = "red"
>>> myBall.size = "big"
使用一个方法
>>> myBall.bounce()
```

配图来自Twitter：@chengr28

![配图14](https://wiki.huihoo.com/images/f/f8/Devopsgirls14.jpg)
