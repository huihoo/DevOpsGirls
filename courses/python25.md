# 第25课：Django web框架概述


### 简介
简单讲，Django 是一个模型-模板-视图（model-template-view，MTV）框架。

$ pip install django

```
$ python -m django --version 或
>>> import django
>>> print(django.get_version())
2.1.5
```

### 运行第一个项目
$ django-admin startproject mysite

看看创建了什么
```
mysite/
    manage.py        # 一个让你用各种方式管理Django项目的命令行工具
    mysite/
        __init__.py  # 一个空文件，告诉Python这个目录应该被认为是一个Python包
        settings.py  # Django项目的配置文件
        urls.py      # URL声明，就是网站的目录 
        wsgi.py      # 运行在WSGI兼容的Web服务器上的入口
```
$ python manage.py runserver

http://127.0.0.1:8000

### Why Django
用来构建Web项目的框架很多，为什么选择Django，因为个人觉得Django包含了你构建Web应用需要的所有功能，你不需要太多挑选和各种评估（这个其实是需要很多经验和实践的）而对于大多数开发者，TA们的核心工作就是开发业务和应用系统，快速搭建产品原型和持续迭代。而不用花太多时间去选择，我想这也是我推荐Django的原因。

[DjangoSites](https://www.djangosites.org/) 提供一个不断增长的使用 Django 搭建的网站的列表，有很多开源的网站可直接拿来用。

### PostgreSQL
先安装并启动PostgreSQL，后面的应用都会使用到它。

使用[pgAdmin](https://www.pgadmin.org/)连接和管理PostgreSQL。

安装Psycopgs适配器

$ pip install psycopg2-binary
```
>>> import psycopg2
>>> conn = psycopg2.connect("dbname=test user=postgres password=postgres")
>>> cur = conn.cursor()
>>> cur.execute("CREATE TABLE test (id serial PRIMARY KEY, num integer, data varchar);")
>>> cur.execute("INSERT INTO test (num, data) VALUES (%s, %s)", (10, "python"))
>>> cur.execute("INSERT INTO test (num, data) VALUES (%s, %s)", (11, "rust"))
>>> cur.execute("SELECT * FROM test;")
>>> cur.fetchall()
[(8, 10, 'python'), (9, 11, 'rust')]
>>> conn.commit() # 写入数据库，打开数据库看插入了两条记录
>>> cur.close()
>>> conn.close()
```
配图来自Twitter：@neku_draw

![配图25](https://wiki.huihoo.com/images/3/3c/Devopsgirls25.jpg)
