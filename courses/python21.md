# 第21课：测试（Testing）（一）

先回顾一下[第8课：错误、异常](python08.md)的内容

### unittest
unittest是Python用于单元测试的标准模块。

先运行一个简单的单元测试，感受下：
```
>>> import unittest
>>> 
>>> class MyTest(unittest.TestCase):
...     pass
... 
>>> if __name__ == '__main__':
...     unittest.main()
... 

----------------------------------------------------------------------
Ran 0 tests in 0.000s
```
再来一个复杂点的单元测试，运行5个小测试：可忽略、标记、或按照预期运行失败。

unittest模块中的装饰器可用来控制对指定测试方法的处理，如：skip、skipIf、skipUnless、expectedFailure等。

如在macOS上运行以下测试，touch unittestsample.py
```
import unittest
import os
import platform

class Tests(unittest.TestCase):
    def test_0(self):
        self.assertTrue(True)

    @unittest.skip('skipped test')
    def test_1(self):
        self.fail('should have failed!')

    @unittest.skipIf(os.name=='posix', 'Not supported on Unix')
    def test_2(self):
        import winreg

    @unittest.skipUnless(platform.system() == 'Darwin', 'Mac specific test')
    def test_3(self):
        self.assertTrue(True)

    @unittest.expectedFailure
    def test_4(self):
        self.assertEqual(2+2, 5)

if __name__ == '__main__':
    unittest.main()
```

运行这个例子：
```
(venv2) gougou:python huihoo$ python unittestsample.py -v
test_0 (__main__.Tests) ... ok
test_1 (__main__.Tests) ... skipped 'skipped test'
test_2 (__main__.Tests) ... skipped 'Not supported on Unix'
test_3 (__main__.Tests) ... ok
test_4 (__main__.Tests) ... expected failure

----------------------------------------------------------------------
Ran 5 tests in 0.001s

OK (skipped=2, expected failures=1)
```
### doctest
doctest模块会搜索那些看起来像是python交互式会话中的代码片段，然后尝试执行并验证结果。

先运行一个简单的doctext，感受下：
```
>>> if __name__ == "__main__":
...     import doctest
...     doctest.testmod()
... 
TestResults(failed=0, attempted=0)
```
再来一个稍微复杂点的例子，创建一个doctestsample.py文件，有两个测试用例，包含以下内容：
```
def add(a, b):
    """
    >>> add(1, 2)
    3
    >>> add('python ', 'rust')
    'python rust'
    """
    return a + b
if __name__=='__main__':
    import doctest
    doctest.testmod()
```

运行这个例子：
```
python -m doctest -v doctestsample.py #  -m 表示引用一个模块，-v 等价于 verbose=True
python doctestsample.py -v

运行结果：
Trying:
    add(1, 2)
Expecting:
    3
ok
Trying:
    add('python ', 'rust')
Expecting:
    'python rust'
ok
1 items had no tests:
    __main__
1 items passed all tests:
   2 tests in __main__.add
2 tests in 2 items.
2 passed and 0 failed.
Test passed.

```

### py.test
安装 pip install pytest

创建pytestsample.py文件，包含：
```
def inc(x):
    return x + 1

def test_answer():
    assert inc(3) == 5
```

运行测试：
```
$ pytest pytestsample.py 
================================= test session starts ======================================
platform darwin -- Python 3.7.1, pytest-4.2.0, py-1.7.0, pluggy-0.8.1
rootdir: /private/tmp/python, inifile:
collected 1 item                                                                                                                                                                                                                                 
pytestsample.py F                                                                          [100%]

================================= FAILURES ===================================
_________________________________ test_answer ___________________________________

    def test_answer():
>       assert inc(3) == 5
E       assert 4 == 5
E        +  where 4 = inc(3)

pytestsample.py:5: AssertionError
================================ 1 failed in 0.45 seconds ========================================

```
### mock
在单元测试中，模拟对象可以模拟复杂的、真实的（非模拟）对象的行为， 如果真实的对象无法放入单元测试中，使用模拟对象就很有帮助。

为什么要用mock?

在下面的情形，可能需要使用模拟对象来代替真实对象：

* 真实对象的行为是不确定的（例如，当前的时间或当前的温度）；
* 真实对象很难搭建起来；
* 真实对象的行为很难触发（例如，网络错误）；
* 真实对象速度很慢（例如，一个完整的数据库，在测试之前可能需要初始化）；
* 真实的对象是用户界面，或包括用户界面在内；
* 真实的对象使用了回调机制；
* 真实对象可能还不存在；
* 真实对象可能包含不能用作测试（而不是为实际工作）的信息和方法。

从Python 3.3开始，mock模块已经被合并到标准库中，被命名为unittest.mock

from unittest import mock

在Python 3.3以前版本，需要安装，pip install mock

import mock

先感受下mock
```
>>> from unittest.mock import MagicMock
>>> mock = MagicMock(side_effect=[1, 2, 3])
>>> mock()
1
>>> mock()
2
>>> mock()
3
```

Mock这块内容会比较多，以后再深入展开。

今天是大年初三，顺祝大家2019，新年快乐！

配图来自Twitter：@chengr28

![配图21](https://wiki.huihoo.com/images/4/4e/Devopsgirls21.jpg)