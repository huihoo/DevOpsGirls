# 第45课：序列化

### 简介
Django 序列化框架提供了一种将 Django 模型转换为其他格式的机制。

Django 支持的序列化格式有：
* XML
* JSON
* YAML

### 序列化
```
>>> from django.core import serializers
>>> with open("person.xml", "w") as out:
...     xml_serializer.serialize(Person.objects.all(), stream=out)
```
这时在目录下生成了 person.xml，内容如下：
```
<?xml version="1.0" encoding="utf-8"?>
<django-objects version="1.0">
    <object model="polls.person" pk="1">
        <field name="first_name" type="CharField">Allen</field><field name="last_name" type="CharField">Long</field>
    </object>
    <object model="polls.person" pk="2">
        <field name="first_name" type="CharField">Peter</field><field name="last_name" type="CharField">Chen</field>
    </object>
</django-objects>
```
试试 JSON 格式：
```
>>> from django.core.serializers import serialize
>>> with open("person.json", "w") as out:
...     serialize('json', Person.objects.all(), stream=out)
```
目录下生成了 person.json，内容如下：
```
[
    {
        "model": "polls.person", 
        "pk": 1, 
        "fields": {
            "first_name": "Allen", "last_name": "Long"
        }
    }, 
    {
        "model": "polls.person", 
        "pk": 2, 
        "fields": {
            "first_name": "Peter", "last_name": "Chen"
        }
    }
]
```

### 反序列化

配图来自Twitter：@ukiukisoda

![配图45](https://wiki.huihoo.com/images/2/24/Devopsgirls45.png)
