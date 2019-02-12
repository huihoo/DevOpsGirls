# 第49课：加密签名

背景：Web 应用安全的黄金法则是永远不要信任来自不受信任来源的数据。 

Django 既提供用于签名值的低级 API，也提供用于设置和读取签名cookie的高级 API。

### SECRET_KEY
使用 startproject 创建 Django 项目时，会自动生成 settings.py 文件并获取随机的 SECRET_KEY 值。 此值是保护签名数据的关键，其安全至关重要，因为攻击者可以使用它来生成自己的签名值。

类似这样的一个值：SECRET_KEY = 'c=$*+jdept%gz2a+b(dasdfdsczc5&&2q&gasdfeasy#1j='

### 使用API
```
>>> from django.core.signing import Signer
>>> signer = Signer()
>>> value = signer.sign('python')
>>> value
'python:Gl-at2uNL427Vt2IuODkwD93Tzc'
>>>

>>> original = signer.unsign(value)
>>> original
'python'
```

配图来自Twitter：@tomo_3

![配图49](https://wiki.huihoo.com/images/thumb/8/87/Devopsgirls49.jpg/1280px-Devopsgirls49.jpg)