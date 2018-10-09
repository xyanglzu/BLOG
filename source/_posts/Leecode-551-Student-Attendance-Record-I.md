---
title: Leecode-551.Student Attendance Record I
toc: true
date: 2018-09-15 13:44:19
tags: 字符串
categories: Leecode
---

# 题目

给定一个字符串来代表一个学生的出勤纪录，这个纪录仅包含以下三个字符：

1. **'A'** : Absent，缺勤
2. **'L'** : Late，迟到
3. **'P'** : Present，到场

如果一个学生的出勤纪录中不**超过一个'A'(缺勤)**并且**不超过两个连续的'L'(迟到)**,那么这个学生会被奖赏。

你需要根据这个学生的出勤纪录判断他是否会被奖赏。

**示例 1:**

```
输入: "PPALLP"
输出: True
```

**示例 2:**

```
输入: "PPALLL"
输出: False
```

# 代码

*对字符串扫描一遍，如果是A就计数器A加1，*

```python
class Solution(object):
    def checkRecord(self, s):
        """
        :type s: str
        :rtype: bool
        """
        slist = list(s)
        count_a = 0
        count_l = 0
        for i in range(len(slist)):
            if slist[i] == 'A':
                count_a += 1
                if count_a > 1:
                    return False
            if slist[i] == 'L':
                count_l += 1
                if count_l > 2:
                    return False
            else:
                count_l = 0
        return True
```

