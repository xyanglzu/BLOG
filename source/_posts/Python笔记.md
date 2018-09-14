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

# 正则表达式

## 正则表达式模式

|      模式      |                             含义                             |
| :------------: | :----------------------------------------------------------: |
|       ^        |                       匹配字符串的开头                       |
|       $        |                       匹配字符串的末尾                       |
|       .        |                         匹配任意字符                         |
|     [...]      |          用来表示一组字符，如[amk]匹配'a', 'm', 'k'          |
|     [^...]     |     不在[]中的字符，如[\^abc]匹配不是'a', 'b', 'c'的字符     |
|      re*       |                     匹配0个或多个表达式                      |
|      re+       |                     匹配1个或多个表达式                      |
|      re?       |                      匹配0个或1个表达式                      |
|     re{n}      | 精确匹配n个前面表达式，如o{2}不能匹配'Bob'中的'o'，但是能匹配‘food'中的两个o |
|     re{n,}     | 匹配n个及n个以上前面表达式，如o{2,}不能匹配'Bob'中的'o'，但是能匹配'fooood'中的所有o |
|    re{n,m}     |                       匹配n到m次表达式                       |
|      a\|b      |                           匹配a或b                           |
|      (re)      |               匹配括号中的表达式，也表示一个组               |
|       \w       |                     匹配字母数字或下划线                     |
|       \W       |                     匹配非字母数组下划线                     |
|       \s       |                       匹配任意空白字符                       |
|       \S       |                      匹配任意非空白字符                      |
|       \d       |                         匹配任意数字                         |
|       \D       |                        匹配任意非数字                        |
|       \b       | 匹配一个单词的边界，即单词和空格的位置。例如'er\b'可匹配'never'的'er'，但不可匹配'verb'中的'er' |
|    \1...\9     |                     匹配第n个分组的内容                      |
| (?P\<name\>re) |        name是一个合法的标识符，name为匹配表达式的名字        |

## re模块

### re.compile方法

*compile 函数用于编译正则表达式，生成一个 Pattern 对象*

#### 语法

```python
re.compile(pattern[, flag])
```

#### 参数

| 参数    | 描述                       |
| ------- | -------------------------- |
| pattern | 一个字符串形式的正则表达式 |
| flag    | 可选参数，正则表达式修饰符 |

#### 返回值

返回一个pattern对象，常有match/search/findall/finditer/split/sub/subn等方法

#### 例子

```python
import re

# 将正则表达式编译成 Pattern 对象 
pattern = re.compile(r'\d+')
```


### re.match方法

*尝试从字符串的起始位置匹配一个模式，如果不是起始位置匹配成功的话，match()返回None*

#### 语法:

```python
re.match(pattern, string, flags=0)
```

#### 参数

| 参数    | 描述                                                         |
| ------- | ------------------------------------------------------------ |
| pattern | 匹配的正则表达式                                             |
| string  | 要匹配的字符串                                               |
| flags   | 标志位，用于控制正则表达式的匹配方式，如：是否区分大小写，多行匹配等。 |

#### 返回值

匹配成功re.match方法返回一个匹配的对象，否则返回None。

我们可以使用group(num) 或 groups() 匹配对象函数来获取匹配表达式。

| 匹配对象方法 | 描述                                                         |
| ------------ | ------------------------------------------------------------ |
| group(num=0) | 匹配的整个表达式的字符串，group() 可以一次输入多个组号，在这种情况下它将返回一个包含那些组所对应值的元组。 |
| groups()     | 返回一个包含所有小组字符串的元组，从 1 到 所含的小组号。     |

#### 例子

```python
#!/usr/bin/python
# -*- coding: UTF-8 -*- 
import re
print(re.match('www', 'www.runoob.com').span()) # 在起始位置匹配
print(re.match('com', 'www.runoob.com')) # 不在起始位置匹配

# 输出
# (0, 3)
# None
```

### re.search方法

*re.search 扫描整个字符串并返回第一个成功的匹配*

#### 语法

```python
re.search(pattern, string, flags=0)
```

#### 参数

| 参数    | 描述                                                         |
| ------- | ------------------------------------------------------------ |
| pattern | 匹配的正则表达式                                             |
| string  | 要匹配的字符串                                               |
| flags   | 标志位，用于控制正则表达式的匹配方式，如：是否区分大小写，多行匹配等。 |

#### 返回值

同上

#### 例子

```python
#!/usr/bin/python
# -*- coding: UTF-8 -*- 
import re
print(re.search('www', 'www.runoob.com').span()) # 在起始位置匹配
print(re.search('com', 'www.runoob.com').span()) # 不在起始位置匹配

# 输出
# (0, 3)
# (11, 14)
```

### re.sub方法

*Python 的 re 模块提供了re.sub用于替换字符串中的匹配项*

#### 语法

```python
re.sub(pattern, repl, string, count=0, flags=0)
```

#### 参数

| 参数    | 描述                                                |
| ------- | --------------------------------------------------- |
| pattern | 正则中的模式字符串                                  |
| repl    | 替换的字符串，也可为一个函数                        |
| string  | 要被查找替换的原始字符串                            |
| count   | 模式匹配后替换的最大次数，默认 0 表示替换所有的匹配 |

#### 返回值

同上

#### 例子

```python
#!/usr/bin/python
# -*- coding: UTF-8 -*-
import re
phone = "2004-959-559 # 这是一个国外电话号码"
# 删除字符串中的 Python注释 
num = re.sub(r'#.*$', "", phone)
print "电话号码是: ", num
# 删除非数字(-)的字符串 
num = re.sub(r'\D', "", phone)
print "电话号码是: ", num

# 输出
# 电话号码是: 2004-959-559 
# 电话号码是: 2004959559
```

```python
#!/usr/bin/python
# -*- coding: UTF-8 -*-
import re
# 将匹配的数字乘以 2
def double(matched):
    value = int(matched.group('value'))
    return str(value * 2)
s = 'A23G4HFD567'
print(re.sub('(?P<value>\d+)', double, s))

# 输出
# A46G8HFD1134
```

### re.findall方法

*在字符串中找到正则表达式所匹配的所有子串，并返回一个列表，如果没有找到匹配的，则返回空列表*

#### 语法

```python
findall(string[, pos[, endpos]])
```

#### 参数

| 参数   | 描述                                               |
| ------ | -------------------------------------------------- |
| string | 待匹配的字符串                                     |
| pos    | 可选参数，指定字符串的起始位置，默认为 0           |
| endpos | 可选参数，指定字符串的结束位置，默认为字符串的长度 |

#### 返回值

同上

#### 例子

```python
# -*- coding:UTF8 -*-
import re
pattern = re.compile(r'\d+') # 查找数字
result1 = pattern.findall('runoob 123 google 456')
result2 = pattern.findall('run88oob123google456', 0, 10)
print(result1)
print(result2)

# 输出
# ['123', '456']
# ['88', '12']
```

### re.finditer方法

*和 findall 类似，在字符串中找到正则表达式所匹配的所有子串，并把它们作为一个迭代器返回*

#### 语法

```python
re.finditer(pattern, string, flags=0)
```

#### 参数

| 参数    | 描述                                                         |
| ------- | ------------------------------------------------------------ |
| pattern | 匹配的正则表达式                                             |
| string  | 要匹配的字符串。                                             |
| flags   | 标志位，用于控制正则表达式的匹配方式，如：是否区分大小写，多行匹配等等。 |

#### 返回值

同上

#### 例子

```python
# -*- coding: UTF-8 -*-
import re
it = re.finditer(r"\d+","12a32bc43jf3")
for match in it:
	print (match.group() )

# 输出
# 12 
# 32 
# 43 
# 3
```

### re.split方法

*split 方法按照能够匹配的子串将字符串分割后返回列表*

#### 语法

```python
re.split(pattern, string[, maxsplit=0, flags=0])
```

#### 参数

| 参数     | 描述                                                         |
| -------- | ------------------------------------------------------------ |
| pattern  | 匹配的正则表达式                                             |
| string   | 要匹配的字符串                                               |
| maxsplit | 分隔次数，maxsplit=1 分隔一次，默认为 0，不限制次数。        |
| flags    | 标志位，用于控制正则表达式的匹配方式，如：是否区分大小写，多行匹配等等 |

#### 返回值

同上

#### 例子

```python
print re.split('\W+', 'runoob, runoob, runoob.')

# 输出
# ['runoob', 'runoob', 'runoob', '']
```


## 正则表达式修饰符

| 修饰符 | 描述                                                         |
| ------ | ------------------------------------------------------------ |
| re.i   | 使匹配对大小写不敏感                                         |
| re.L   | 做本地化识别（locale-aware）匹配                             |
| re.M   | 多行匹配，影响 ^ 和 $                                        |
| re.S   | 使 . 匹配包括换行在内的所有字符                              |
| re.U   | 根据Unicode字符集解析字符。这个标志影响 \w, \W, \b, \B.      |
| re.X   | 该标志通过给予你更灵活的格式以便你将正则表达式写得更易于理解。 |

