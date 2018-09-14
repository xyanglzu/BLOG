---
title: Leecode-38.Count and Say
toc: true
date: 2018-09-11 15:05:31
tags: 字符串
categories: Leecode
---

# 题目

[Leecode 38 Count and Say](https://leetcode.com/problems/count-and-say/description/)

报数序列是指一个整数序列，按照其中的整数的顺序进行报数，得到下一个数。其前五项如下：

```
1.     1
2.     11
3.     21
4.     1211
5.     111221
```

`1` 被读作  `"one 1"`  (`"一个一"`) , 即 `11`。
`11` 被读作 `"two 1s"` (`"两个一"`）, 即 `21`。
`21` 被读作 `"one 2"`,  "`one 1"` （`"一个二"` ,  `"一个一"`) , 即 `1211`



给定一个正整数 *n* ，输出报数序列的第 *n* 项。

注意：整数顺序将表示为一个字符串。



示例1：

```
输入: 1
输出: "1"
```

示例2：

```
输入: 4
输出: "1211"
```

# 代码

## 解法1：

*n=1时，$result_1$为`'1'`;计算n时，通过扫描$result_{n-1}$ 字符串，统计连续相同的数字s，并将该数字的个数count及自身s拼接在最终结果中。*

```python
class Solution(object):
    def countAndSay(self, n):
        """
        :type n: int
        :rtype: str
        """
        result = "1"
        for i in range(2, n+1):
            count = 1
            cur = result[0]
            tmp = ""
            for j in range(1, len(result)):
                if result[j] == cur:
                    count += 1
                else:
                    tmp += str(count) + cur
                    count = 1
                    cur = result[j]
            tmp += str(count) + cur
            result = tmp
        return result
```

## 解法2：

*利用正则表达式的替换方法*

- *re.sub中的函数参数，目的是计算相同数字的个数，将个数与数字拼接*
- *正则表达式*`r'(.)\1*'`*匹配一个或多个等于group(1)的字符，如'11122'，group(1)就是字符'1'，匹配该字符多次，即'111'*
- *re.sub实现将匹配到的*

```python
class Solution(object):
    def countAndSay(self, n):
        s = '1'
        for _ in range(n - 1):
            s = re.sub(r'(.)\1*', lambda m: str(len(m.group(0))) + m.group(1), s)
        return s
```

## 解法3：

*正则表达式*`r'((.)\2*)`，第一个括号里面是group(1)——连续相同的字符，第二个括号里面是group(2)——单个字符，因此re.findall返回了group(1)与group(2)的列表

```python
def countAndSay(self, n):
    s = '1'
    for _ in range(n - 1):
        s = ''.join(str(len(group)) + digit
                    for group, digit in re.findall(r'((.)\2*)', s))
    return s
```

## 解法4：

*itertools.groupby将字符串s将连续相同字符分为一组，每一组包括了字符及其对应的连续字符列表，如：*

```python
for digit, group in itertools.groupby("111221"):
	print digit, list(group)

1 ['1', '1', '1']
2 ['2', '2']
1 ['1']
```



```python
def countAndSay(self, n):
    s = '1'
    for _ in range(n - 1):
        s = ''.join(str(len(list(group))) + digit
                    for digit, group in itertools.groupby(s))
    return s
```

