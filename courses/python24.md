# 第24课：领域特定语言（Domain-specific language，DSL）

领域特定语言（domain-specific language、DSL）指的是专注于某个应用程序领域的计算机语言，如SQL语言，正则表达式。

DSL分为两类：
* 内部DSL(Internal DSL)，DSL和宿主语言是相同的语言。
* 外部DSL(External DSL)，DSL和宿主语言不同，需要自己写解释器。

抛个问题先：世界上最强大的 DSL 实现语言，不是 Haskell 或者 Scala，而应该是 Scheme？

看不懂没关系，留在以后思考。

### 为什么有DSL
通用语言在解决某些特定领域的问题有时会显得有些吃力，这时候DSL似乎就有了用武之地。

个人感觉，若能在某些特定领域拥有比其它同学更简单、更高效的解决方法和手段，也是自己的一个加分项和优势。

### Python DSL
Python是一门通用、灵活、高效的语言，它在解决某些特定领域问题时会比较擅长。

目前，Python是数据科学和机器学习领域的明星语言，这些也都源于它所具有的语言特性和优势。

### 参考例子 
一个简单的Internal DSL for SQL DDL。
```
from contextlib import contextmanager

class Table(object):
    def __init__(self, table_name):
        self.table_name = table_name
        self.fields = {}

    def __getattr__(self, name):
        def f(**kvs):
            self.fields[name] = kvs
        return f

    def execute(self):
        print ("Creating table %s with fields %s"%(self.table_name, self.fields))

@contextmanager
def create_table(table_name):
    table = Table(table_name)
    yield table
    table.execute()

with create_table('User') as t:
    t.first_name(type='char', length=30)
    t.last_name(type='char', length=30)
    t.age(type='int')

运行结果：
Creating table User with fields {'first_name': {'type': 'char', 'length': 30}, 'last_name': {'type': 'char', 'length': 30}, 'age': {'type': 'int'}}

```

### 参考
* [王垠《聊聊 DSL》](http://www.yinwang.org/blog-cn/2017/05/25/dsl)
* [Creating Domain Specific Languages in Python](https://www.slideshare.net/Siddhi/creating-domain-specific-languages-in-python)
* [Domain-specific languages to Manycore and GPU: Building High-Performance Tools with Python](https://github.com/inducer/languages-and-codegen-tutorial)
* [Writing a Domain Specific Language (DSL) in Python](https://dbader.org/blog/writing-a-dsl-with-python)

配图来自Twitter：@makadamixa

![配图24](https://wiki.huihoo.com/images/thumb/8/8e/Devopsgirls24.jpg/800px-Devopsgirls24.jpg)
