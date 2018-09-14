---
title: 剑指offer-反转链表
toc: true
date: 2018-09-09 15:28:55
tags: 链表
categories: 剑指offer
---

# 题目

输入一个链表，反转链表后，输出新链表的表头。

[题目链接](https://www.nowcoder.com/practice/75e878df47f24fdc9dc3e400ec6058ca?tpId=13&tqId=11168&tPage=1&rp=1&ru=%2Fta%2Fcoding-interviews&qru=%2Fta%2Fcoding-interviews%2Fquestion-ranking)

# 思路

原地转换链表，需要三个指针，一个保存当前结点current，一个保存上一个结点pre，一个保存下一个结点next。

# 代码

**python代码**

```python
# -*- coding:utf-8 -*-
# class ListNode:
#     def __init__(self, x):
#         self.val = x
#         self.next = None


class Solution:
    # 返回从尾部到头部的列表值序列，例如[1,2,3]
    def ReverseList(self, pHead):
        if not pHead or not pHead.next:
            return pHead

        pre = None
        current = pHead
        next = None

        while current is not None:
            next = current.next
            current.next = pre
            pre = current
            current = next
        return pre
```

