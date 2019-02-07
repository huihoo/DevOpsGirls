# 第23课：设计模式（Design patterns）
在这里放出设计模式，好像不是特别合适，但直觉是早一点了解些设计模式，对之后的提高是很有帮助的。

### 设计模式
在软件工程中，设计模式（design pattern）是对软件设计中普遍存在（反复出现）的各种问题，所提出的解决方案。设计模式并不直接用来完成代码的编写，而是描述在各种不同情况下，要怎么解决问题的一种方案。

![设计模式](https://wiki.huihoo.com/images/thumb/a/a2/Design-pattern.png/1280px-Design-pattern.png) 
[点击下载大图](https://wiki.huihoo.com/images/a/a2/Design-pattern.png)

图片来自[icemoon1987](http://www.cnblogs.com/icemoon1987/p/3349415.html)

经典的《设计模式：可复用面向对象软件的基础》包含23个设计模式，这本书是软件工程领域有关软件设计的一本重要的书，提出和总结了对于一些常见软件设计问题的标准解决方案，称为软件设计模式。该书作者为：埃里希·伽玛（Erich Gamma）, Richard Helm , Ralph Johnson，John Vlissides，后以“四人帮”（Gang of Four，GoF）著称。

先这23个设计模式罗列一下，以后需要的可继续深入下去。

### 创建范例
创建范例全部是关于如何创建实例的。这组范例可以被划分为两组：类创建范例及对象创建范例。类创建实例在实例化过程中有效的使用类之间的继承关系，对象创建范例则使用代理来完成其任务。

* 抽象工厂 (Abstract Factory pattern)
* 构造器 (Builder pattern)
* 工厂方法 (Factory Method pattern)
* 原型 (Prototype pattern)
* 单例模式 (Singleton pattern)

### 结构范例
这组范例都是关于类及对象复合关系的。

* 适配器(Adapter pattern)
* 桥接(Bridge pattern)
* 组合(Composite pattern)
* 装饰(Decorator pattern)
* 外观(Façade pattern)
* 享元(Flyweight pattern)
* 代理(Proxy pattern)

### 行为范例
这组范例都是关于对象之间如何通讯的。

* 职责链(Chain-of-responsibility pattern)
* 命令(Command pattern)
* 解释器(Interpreter pattern)
* 迭代器(Iterator pattern)
* 中介者(Mediator pattern)
* 备忘录(Memento pattern)
* 观察者(Observer pattern)
* 状态机(State pattern)
* 策略(Strategy pattern)
* 模板方法(Template method pattern)
* 访问者(Visitor pattern)

### 例子

### python-patterns
https://github.com/faif/python-patterns

通过这个项目来介绍一下设计模式

这块内容有点多，以后单独深入展开。

### 参考
* [Design Patterns](https://sourcemaking.com/design_patterns)

配图来自Twitter：@chengr28

![配图23](https://wiki.huihoo.com/images/2/26/Devopsgirls23.jpg)
