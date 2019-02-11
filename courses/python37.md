# 第37课：模板（一）
模板提供了一个对设计师友好的语法用于渲染向用户呈现的信息，这里涉及如何使用语法以及如何扩展的内容。

Django 项目可以配置一个或多个模板引擎，Django后端内置一个自己的模板系统：Django template language（DTL） `</ref/templates/language>` 。当然，也可以使用第三方模版引擎，如：jinja2

Django 定义了一个标准的API，用于加载和渲染模板，而不用考虑后端的模板系统。加载包括查找给定标识符的模板并对其进行预处理，通常将其编译的结果保存在内存中。渲染工具将上下文数据插入模板并返回结果字符串。

### 概念
* Engine
django.template.Engine 封装了 Django 模板系统的一个实例，实例化引擎的主要原因是在 Django 项目之外直接使用 Django 模板语言。

django.template.backends.django.DjangoTemplates 是一个包装器（wrapper），它将 django.template.Engine 适配成 Django 的模板后端API。
* Template
django.template.Template 是已编译的模板，使用 Engine.get_template() 或 Engine.from_string() 获取模板

同样，django.template.backends.django.Template 是一个包装器（wrapper），它将 django.template.Template 适配成公共模板API。

* Context
除了上下文数据外，django.template.Context 还包含一些元数据（metadata）， 它被传递给 Template.render() 用于渲染模板。

django.template.RequestContext 是 Context 的子类，它存储当前 HttpRequest 并运行模板上下文处理器（template context processors）。

* Loaders
模板加载器负责定位模板，加载模板和返回模板对象。Django 提供了几个内置模板加载器并支持自定义模板加载器。

* Context processors
上下文处理器是接收当前 HttpRequest 作为参数的函数，并返回一个添加数据到渲染上下文的字典。它们的主要用途是将所有模板共享的公共数据添加到上下文中，而不用在每个视图中重复代码。

Django 提供了许多内置的上下文处理器，实现自定义上下文处理器就像定义函数一样简单。

### 配置
mysite/settings.py
```
TEMPLATES = [
    {
        'BACKEND': 'django.template.backends.django.DjangoTemplates',
        'DIRS': [os.path.join(BASE_DIR, 'templates')],
        'APP_DIRS': True,
        'OPTIONS': {
            'context_processors': [
                'django.template.context_processors.debug',
                'django.template.context_processors.request',
                'django.contrib.auth.context_processors.auth',
                'django.contrib.messages.context_processors.messages',
            ],
        },
    },
]
```
也可多配置一个模版系统，如：jinja2
```
    {
        'BACKEND': 'django.template.backends.jinja2.Jinja2',
        'DIRS': [
            '/home/html/jinja2',
        ],
    },
```
### 简单使用
为了减少加载和渲染模板的重复性，Django 提供了一个自动处理的快捷函数：render_to_string()
```
from django.template.loader import render_to_string
rendered = render_to_string('my_template.html', {'foo': 'bar'})
```

此外，你可以在 Django 项目之外直接使用配置好的模版引擎：
```
from django.template import engines

django_engine = engines['django']
template = django_engine.from_string("Hello {{ name }}!")
```

配图来自Twitter：@chengr28

![配图37](https://wiki.huihoo.com/images/thumb/3/3f/Devopsgirls37.jpg/684px-Devopsgirls37.jpg)
