---
title: Python笔记
toc: true
date: 2018-07-03 10:25:31
tags:
categories: Python
---

# 基本语法规则

## 创建

第一行`#!/usr/bin/python`指定解释器（或者用`#!/usr/bin/envpython`更有移植性）；

要让python支持中文，需要加上`# -*- coding: utf-8 -*-`（Python3默认是utf-8编码）；

```python
#!/usr/bin/env python 或 #!/usr/bin/python
# -*- coding: utf-8 -*-
```

## 注释

单行注释用`#`；

借助三引号将注释代码定义为多行字符串：

```python
"""
···注释内容
"""

'''
···注释内容
'''
```

## 变量

### (1) 数值类型

1. 整型：包括布尔值`True, False`。 八进制以`0`开头。十六进制以`0x(X)`开头；
2. 长整型：无限大小的数（受限于虚拟内存），结尾添加`l`或`L`
3. 浮点型：十进制或科学计数法（`e或E`表示10），如`5.0e-2`
4. 复数：实数部分+虚数部分`j/J`，如`7+3j`

相关模块

```python
numbers     # Numeric abstract base classes
math        # Mathematical functions
cmath       # Mathematical functions for complex numbers
decimal     # Decimal fixed point and floating point arithmetic
fractions   # Rational numbers
random      # Generate pseudo-random numbers
itertools   # Functions creating iterators for efficient looping
functools   # Higher-order functions and operations on callable objects
operator    # Standard operators as functions
```



### (2) 字符串

相关模块

```python
string    # Common string operations
re        # Regular expression operations
```



### (3) 元组Tuple

不可变的List

### (4) 列表List

list可作为队列，也可以作栈

```python
list.append(x)     # Equivalent to a[len(a):] = [x].
list.extend(L)     # Equivalent to a[len(a):] = L.
list.insert(i, x)  # a.insert(0, x) inserts at the front of the list
list.remove(x)     # Remove the first item from the list whose value is x. 
list.pop([i])      # a.pop() removes and returns the last item in the list. 
list.clear()       # Equivalent to del a.
list.index(x)      # Return the index of the first item whose value is x. 
list.count(x)      # Return the number of times x appears in the list.
list.sort()        # Sort the items of the list in place.
list.reverse()     # Reverse the elements of the list in place.
list.copy()        # Return a shallow copy of the list. Equivalent to a."""
```



### (5) 字典dict

键-值对的集合，键和值可以是任意对象，如`d={1:"a", 2:"b"}`

## 打印信息

Pyhon3.x去除了print语句，以print()函数代替。

```python
print(*objects, sep=' ', end='\n', file=sys.stdout, flush=False)
```

print函数支持可变参数(*objects)，参数间默认以空格分隔，输出默认以一个换行符结束，默认输出到标准输出，默认不清空缓存。如：`print("aaa", "bbb", sep='\t', end='!!!')`



格式化输出字符串，一种方法是百分号格式化字符串：

```python
# "字符 %格式1 %格式2 字符" %(变量1,变量2)   理解成：前两个%是占位符，后面是变量替换
print("His age is %d" %(25), "bbb")
# 输出信息如下
# His age is 25 bbb
```

还有一种方法，可以用内置函数[format](https://docs.python.org/3/library/functions.html?highlight=format#format)，使用方法如下：

```python
print("This kind of {tea}".format(tea="Tie Guanyin"))
# 输出信息如下
# This kind of Tie Guanyin
```

## 下划线

```python
# 变量
_xxx      # 标明是一个私有变量, 只用于标明, 外部类还是可以访问到这个变量
__xxx     # 类中私有变量
__xxx__   # 内置变量，系统定义的名字，如__init__()代表类的构造函数
XXX_XXX   # 不会发生改变的全局变量
 
# 函数
_xxx     # 标明是一个私有函数, 只用于标明
__xxx__  # 标明是特殊函数，如操作符重载
```

**注：使用”from mymodule import *”加载模块时，不会加载以单下划线开头的模块属性。**

## 调用Shell命令

```python
import os
os.system(cmd)  # 只返回命令运行结果，不过取不了返回值
os.popen(cmd)   # 要得到命令的输出内容，只需再调用下read()或readlines()等,如：os.popen(cmd).read()
 
import commands                 # 其实是对popen的封装
commands.getstatusoutput(cmd)   # 返回(status, output).
commands.getoutput(cmd)         # 只返回输出结果
commands.getstatus(file)        # 返回ls -ld file的执行结果字符串
```

## 命令行参数传递

有时候需要向python脚本文件传递参数(如文件名)，python利用模块sys.argv，sys.argv实为一个List，存储所有命令行参数，sys.argv[0]是脚本名称本身，len(sys.argv)可以得到总参数个数。举例如下：

```python
# 运行脚本
python test.py arg1 arg2
 
# python脚本
#!/usr/bin/env python
import sys
if len(sys.argv) < 3 :
    sys.exit(0)
arg1 = int(sys.argv[1])
arg2 = float(sys.argv[1])
```

## 条件表达式

### 布尔操作

```python
x or y         # if x is false, then y, else x
x and y        # if x is false, then x, else y
not x          # if x is false, then True, else False
```

### 比较符

```python
<         # strictly less than
<=        # less than or equal
>         # strictly greater than
>=        # greater than or equal
==        # equal
!=        # not equal
is        # object identity
is not    # negated object identity
```

### 整数位操作

```python
x | y         # bitwise or of x and y     
x ^ y         # bitwise exclusive or of x and y     
x & y         # bitwise and of x and y     
x << n        # x shifted left by n bits
x >> n        # x shifted right by n bits
~x            # the bits of x inverted
```

### 数值操作

```python
-x     # x negated
+x     # x unchanged
x + y            #sum of x and y
x - y            #difference of x and y
x * y            # product of x and y
x / y            # quotient of x and y
x // y           # floored quotient of x and y
x % y            # remainder of x / y
divmod(x, y)   # the pair (x // y, x % y)
pow(x, y)        # x to the power y
x ** y           # x to the power y
 
abs(x)           # absolute value or magnitude of x
int(x)           # x converted to integer
float(x)   # x converted to floating point
complex(re, im)  # a complex number with real part re, imaginary part im. imdefaults to zero.
c.conjugate()    # conjugate of the complex number c
```

### 序列操作list, tuple, range

```python
x in s        # True if an item of s is equal to x, else False
x not in s    # False if an item of s is equal to x, else True
 
s + t            # the concatenation of s and t
s * n or n * s    # n shallow copies of s concatenated
 
s[i]        # ith item of s, origin 0
s[i:j]        # slice of s from i to j
s[i:j:k]    # slice of s from i to j with step k
 
len(s)    # length of s
min(s)    # smallest item of s
max(s)    # largest item of s
 
s.index(x[, i[, j]])    # index of the first occurrence of x in s (at or after index i and before index j)
 
s.count(x)    # total number of occurrences of x in s
```

