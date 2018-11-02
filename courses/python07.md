# 第7课：文件、目录

将以下内容以Jupyter Notebook的方式做练习和自己总结，并保存.ipynb。  

touch text.txt
* 列举目录文件 
* 写文件
* 读文件

本节课主要学习目录操作和文件读写。

```
#目录操作
>>> import os
>>> os.getcwd()

#改变Linux/macOS目录
>>> os.chdir('/Users/huihoo/Software')

#改变Windows目录
>>> os.chdir('C:\\Windows\System32')

#继续试试创建目录：makedirs 

#列举目录文件
>>> from pathlib import Path
>>> p = Path('.')
>>> list(p.glob('*.*'))
or 
>>> for child in p.iterdir(): child

#写文件
with open('test.txt', 'w', encoding='utf-8') as f:
    f.write('test')
    f.close()
```

注意：一定要close()关闭文件，否则你做得修改没有保存到文件里，但写入的内容会覆盖以前的文件内容。

所以，我们想追加写入文件，我们使用’a’追加模式
```
with open('test.txt', 'a', encoding='utf-8') as f:
    f.write(‘\n输入中文’)
    f.close()

#读文件
with open('test.txt', 'r', encoding='utf-8') as f:
    f.readlines()
```

还有很多文件目录操作的模块和函数，大家都去了解下。

扩展学习：文件目录的相关模块和函数，大家可搜索网络完成一些文件目录扩展练习。
```
>>> help()
help> modules
pathlib, os.path, tempfile, filecmp, fileinput, shutil, zipfile

#os模块：提供了与系统、目录操作相关的函数
>>>import os
>>>dir(os)

#pathlib模块：其提供的Path类可以创建path路径对象, 属于比os.path更高抽象级别的对象。
>>> import pathlib
>>> dir(pathlib)
阅读：Python 3的pathlib模块：驯服文件系统

#os.path模块：包含许多与文件名和文件路径相关的函数
>>> import os.path
>>> dir(os.path)

#tempfile模块：临时文件和目录处理
>>> import tempfile
>>> dir(tempfile)

#filecmp模块：用于比较文件及文件夹的内容
>>> import filecmp
>>> dir(flecmp)

#fileinput模块：可以对一个或多个文件中的内容进行迭代、遍历等操作，其input()函数有点类似文件
#readlines()方法，区别在于前者是一个迭代对象，需要用for循环迭代，后者是一次性读取所有行。
>>>import fileinput
>>>dir(fileinput)

#shutil模块：复制、移动、改名和删除文件
>>> import shutil, os
>>> dir(shutil)

#zipfile模块：压缩文件
>>> import zipfile, os
>>> dir(zipfile)
```

配图来自Twitter：@momoco_haru

![配图7](https://wiki.huihoo.com/images/b/b5/Devopsgirls07.jpg)