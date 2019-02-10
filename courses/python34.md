# 第34课：模型（二）

### 管理员
Manager是为Django模型提供的数据库查询接口，Django应用中的每个模型都至少存在一个Manager。
```
```

### 数据库事务
事务是指具有原子性的一系列数据库操作。即使是程序崩溃，数据库也会确保这些操作要么全部完成（commit）要么全部都未执行（rollback）。

Django 默认的事务行为是自动提交。

工作原理：将每个HTTP请求封装在一个事务中，配置中的参数 ATOMIC_REQUESTS 设置为 True。在调用试图方法前，Django 先生成一个事务。如果响应能正常生成，Django 会提交该事务。而如果视图出现异常，Django 则会回滚该事务。

你还可以在视图代码中执行子事务，一般会使用 :func:atomic 上下文管理器。

###

### 数据库函数

配图来自Twitter：@kagachi_SK

![配图34](https://wiki.huihoo.com/images/c/cf/Devopsgirls34.jpg)
