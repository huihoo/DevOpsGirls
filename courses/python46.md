# 第46课：缓存

### 简介
对于动态 Web 网站，每次用户发起的请求，服务器都会计算，从数据库查询、业务逻辑、页面渲染等，这些都会消费计算资源。而缓存就是保存这些计算结果，不用每一次都重新计算，这样就极大的减少了服务端的开销和压力，也会带来性能和用户体验的提升。

Web 应用涉及不同层面的缓存：数据库、文件系统、内存等。
* Memcached
* Database caching
* Filesystem caching
* Local-memory caching
* Dummy caching (for development)

### 缓存API
通过 Django 提供的缓存 API，你可以任意粒度缓存各种 Python 对象：字符串、字典、模型对象列表等。

```
>>> from django.core.cache import cache
>>> cache.set('my_key', 'hello, world!', 30)
>>> cache.get('my_key')
'hello, world!'
>>> cache.get('my_key')
>>> 
没有返回值，因为30秒后，cache已过期（expire）。
```

### Memcached
Memcached 是 Django 原生支持的最快，最有效的缓存类型，它是一个完全基于内存的缓存服务器，所有缓存的数据都存储在内存中，Facebook、Wikipedia 等大型网站使用它来减少数据库访问并显着提高网站性能。

安装完 Memcached 后，你需要安装两个最常见的 Python 包：[python-memcached](https://pypi.org/project/python-memcached/)、pylibmc(https://pypi.org/project/pylibmc/)。

Memcached 有很多的配置方案，这是本地缓存的例子，使用了 python-memcached 绑定。
```
CACHES = {
    'default': {
        'BACKEND': 'django.core.cache.backends.memcached.MemcachedCache',
        'LOCATION': '127.0.0.1:11211',
    }
}
```
### 数据库缓存
需要先在数据库中建立一个用于缓存的数据库表，数据库缓存使用的是你配置文件中的数据库，而不是其他的数据库，本教程指的是 PostgreSQL。

$ python manage.py createcachetable my_cache_table

配置信息
```
CACHES = {
    'default': {
        'BACKEND': 'django.core.cache.backends.db.DatabaseCache',
        'LOCATION': 'my_cache_table',
    }
}
```
### 文件系统缓存
目录使用绝对地址
```
CACHES = {
    'default': {
        'BACKEND': 'django.core.cache.backends.filebased.FileBasedCache',
        'LOCATION': '/var/tmp/django_cache',  # 'LOCATION': 'c:/foo/bar', 这是 Windows 下的目录格式 
    }
}
```

### 本地内存缓存
如果未在设置文件中指定其他缓存方案，则它就是默认缓存。若你想运行类似 Memcached 这样速度优势的方案（但没安装 Memcached），可采用此方案用于开发。

缓存使用最近最少使用（least-recently-used，LRU）策略。

```
CACHES = {
    'default': {
        'BACKEND': 'django.core.cache.backends.locmem.LocMemCache',
        'LOCATION': 'unique-snowflake',
    }
}
```
### 虚拟缓存
虚拟缓存，实际上并不是真实的缓存，它只是实现了缓存接口而不做任何事情，常用于开发/测试中不使用缓存的情况。

```
CACHES = {
    'default': {
        'BACKEND': 'django.core.cache.backends.dummy.DummyCache',
    }
}
```

### 缓存中间件
要注意顺序，因为中间件的顺序决定了运行的顺序。UpdateCache一定要放在第一位，Fetch必须放最后。
```
MIDDLEWARE = [
    'django.middleware.cache.UpdateCacheMiddleware',
    'django.middleware.common.CommonMiddleware',
    'django.middleware.cache.FetchFromCacheMiddleware',
]
```

配图来自Twitter：@tomo_3

![配图46](https://wiki.huihoo.com/images/thumb/3/33/Devopsgirls46.jpg/726px-Devopsgirls46.jpg)