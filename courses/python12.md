# 第12课：程序结构（Program structure）

Python程序由包、模块（即一个Python文件.py）和函数组成，包是由一系列模块组成的集合，模块是处理某一类问题的函数和类的集合。

![python程序结构](https://wiki.huihoo.com/images/b/b6/Python-program-structur.png)

(图片来自：w3cschool.cn)

包中必须至少含有一个__init__.py文件，该文件的内容可以为空。用于标识当前文件夹是一个包。

### 物理设计

* 组件与类

* 依赖关系

* 层次化

* 包

### 逻辑设计

* 构建一个组件

* 设计一个函数

* 实现一个对象

### Web项目结构
一个非常简单的Web站点目录结构：
```
mysite/
    manage.py
    mysite/
        __init__.py
        settings.py
        urls.py
        wsgi.py
```

### 网站架构
组成 Web 网站的核心主要包括模型（数据）、视图（显示）、模版（渲染）、表单（交互）、安全等。

网站支撑软件包括：web server、database等。

### 脚手架
我们将采用 Django 框架，它提供了方便的管理工具，能自动创建项目、应用的目录和初始化文件。

```
创建项目
$ django-admin startproject mysite 

创建应用
$ python manage.py startapp polls

一个项目可包含多个应用
```
配图来自Twitter

![配图12](https://wiki.huihoo.com/images/thumb/e/e8/Devopsgirls12.jpg/1280px-Devopsgirls12.jpg)
