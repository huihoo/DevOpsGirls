# 第9课：语法（Syntax）、语义（Semantics）、词汇（Lexical）（一）

将以下内容以Jupyter Notebook的方式做练习和自己总结，并保存.ipynb。 

这节课我们从以下几点入手，更多了解Python语言的一些基本原理，它们容易理解和掌握，不会很枯燥。

* 语法（Syntax） 
* 语义（Semantics）
* 词汇（Lexical）

这是编程语言都会涉及的几个概念，它们定义了Python语言的规范，大家需了解下。

如： AST（Abstract Syntax Trees）抽象语法树，词法分析（标识符、关键字）。在学习时可对应英语的语法、语义、句法想想，能帮助理解它们大致的意思。

这里先给大家引出两个概念：编译时(Compile time)和运行时(Runtime)

 一个现代编译器的主要工作流程如下： 源代码（source code）→ 预处理器（preprocessor）→ 编译器（compiler）→ 汇编程序（assembler）→ 目标代码（object code）→ 链接器（Linker）→ 可执行文件（executables）
￼

![donnet](https://wiki.huihoo.com/images/thumb/e/e8/Common-Language-Runtime.png/1280px-Common-Language-Runtime.png)

此图是C#的编译过程，其思路也适用于Python语言，Python语法、语义、词汇等概念也贯穿于其中。

通过  Python Language Services 和  Python Runtime Services 标准库服务

Python完成源码的语法解析、抽象语法树处理、访问编译器符号表、编译器编译.py源码成字节码、交由虚拟机运行。和现代编译器的主要工作流程类似。

这里：解释器(interpreter)由字节码编译器和虚拟机组成，虚拟机起着类似运行时的作用。

简单讲就是：字节码编译器、字节码虚拟机。

![python](https://wiki.huihoo.com/images/5/5b/Python-interpreter.png)
￼
Python虚拟机是Python的核心，在.py源代码被字节码编译器编译为字节码指令序列后，将由字节码虚拟机接手，依次读入每一条字节码指令，并在当前的上下文环境中执行这条字节码指令。

参考资料：
* [Python Language Reference](https://docs.python.org/3/reference/index.html) 描述了Python的语法和核心语义。

这节课的主要目的就是大家理解下Python的编译原理和解释过程，下节课我们实际操作下编译过程。

配图来自Twitter：@MacciattoS2

![配图9](https://wiki.huihoo.com/images/thumb/9/9b/Devopsgirls09.png/731px-Devopsgirls09.png)