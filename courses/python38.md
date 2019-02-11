# 第38课：模板（二）

### Django template language（DTL）
了解一些基本语法，这些标签和过滤器可以是内置的，也可以自定义的：
* 变量(variable)：{{ and }}
My first name is {{ first_name }}. My last name is {{ last_name }}.

* 标签(Tags)：{% and %} 
{% if user.is_authenticated %}Hello, {{ user.username }}.{% endif %}

* 过滤器(Filters)：{{ | }}
{{ django|title }}

* 注释(Comments)：{#  and #}
{# this won't be rendered #}

### 自定义标签
注册自定义标签：django.template.Library.simple_tag()
```
import datetime
from django import template
register = template.Library()
@register.simple_tag
def current_time(format_string):
    return datetime.datetime.now().strftime(format_string)
```

### 自定义过滤器
自定义的过滤器就是一些有一到两个参数的Python函数，如：

在过滤器``{{ var|foo:"bar" }}``中，变量``var``和参数``bar``会传递给过滤器``foo``

注册自定义过滤器：django.template.Library.filter()
```
>>> from django import template
>>> register = template.Library()
>>> @register.filter
... def lower(value):
...     return value.lower()
```

配图来自Twitter：@chengr28

![配图38](https://wiki.huihoo.com/images/thumb/b/b7/Devopsgirls38.jpg/727px-Devopsgirls38.jpg)
