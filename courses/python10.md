# 第10课：语法（Syntax）、语义（Semantics）、词法（Lexical）（二）

将以下内容以Jupyter Notebook的方式做练习和自己总结，并保存.ipynb。

Python的编译执行过程其实和Java和C#是类似的，也涉及字节码和虚拟机两个主要概念，这个我们在第9课中有描述。

这节课我们实践操作下如何把Python源文件.py编译成可执行文件的过程。

注意：这里和本系列课程都使用Python3.6进行实验和学习，Python3和Python2两版本有非常大的差异，这里有些环节（pyc和pyo的生成过程）使用了Python2（Python2.7）。

创建helloworld.py文件
```
#!/anaconda3/bin/python
print ("Hello World!")
```

### pyc文件
pyc是由py文件经过编译后生成的二进制文件，是一种跨平台的byte code，再由python虚拟机执行。

需要 py_compile 模块

```
python2 -m py_compile helloworld.py 
生成了 helloworld.pyc 或
>>> import py_compile
>>> py_compile.compile('helloworld.py')
'__pycache__/helloworld.cpython-36.pyc'
```

### pyo文件
pyo是优化编译后的文件
```
python2 -O -m py_compile helloworld.py 
注意：这里使用python2生成pyo
helloworld.pyo
```

### so文件
so是python的动态链接库

创建setup.py
```
from distutils.core import setup
from Cython.Build import cythonize
 
setup(
  ext_modules = cythonize("helloworld.py"),
)
```
python setup.py build_ext --inplace

先将py转换为c代码，然后编译c为so文件。
```
build/temp.macosx-10.7-x86_64-3.6/helloworld.o
helloworld.c
helloworld.cpython-36m-darwin.so 

```
### dis 
dis是Python字节码的反汇编程序（Disassembler）

我们使用dis对python字节码进行解析

```
>>> s = open('helloworld.py').read()
>>> co = compile(s, 'helloworld.py', 'exec')
>>> dis.dis(co)
  1           0 LOAD_NAME                0 (print)
              2 LOAD_CONST               0 ('Hello World!')
              4 CALL_FUNCTION            1
              6 POP_TOP
              8 LOAD_CONST               1 (None)
             10 RETURN_VALUE
```
获得dis帮助
```
>>> help(dis)
```

再完成一个操作
```
>>> def myfunc(alist):
...     return len(alist)
...
>>> bytecode = dis.Bytecode(myfunc)
>>> for instr in bytecode:
...     print(instr.opname)
...
LOAD_GLOBAL
LOAD_FAST
CALL_FUNCTION
RETURN_VALUE
>>>
```
配图来自Twitter：@neku_draw

![配图10](https://wiki.huihoo.com/images/thumb/3/3c/Devopsgirls10.png/682px-Devopsgirls10.png)
