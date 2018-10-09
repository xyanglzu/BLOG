---
title: 链表-从尾到头打印链表
toc: true
date: 2018-09-21 11:20:36
tags: 链表
categories: 剑指offer
---

# 题目

输入一个链表，按链表值从尾到头的顺序返回一个ArrayList。

[题目链接](https://www.nowcoder.com/practice/d0267f7f55b3412ba93bd35cfa8e8035?tpId=13&tqId=11156&tPage=1&rp=1&ru=/ta/coding-interviews&qru=/ta/coding-interviews/question-ranking)

# 思路

通常，这种情况下，我们不希望修改原链表的结构。返回一个反序的链表，这就是经典的“后进先出”，我们可以使用栈实现这种顺序。每经过一个结点的时候，把该结点放到一个栈中。当遍历完整个链表后，再从栈顶开始逐个输出结点的值，给一个新的链表结构，这样链表就实现了反转。

# 代码

```python
# -*- coding:utf-8 -*-
# class ListNode:
#     def __init__(self, x):
#         self.val = x
#         self.next = None
 
class Solution:
    # 返回从尾部到头部的列表值序列，例如[1,2,3]
    def printListFromTailToHead(self, listNode):
        # write code here
        result = []
        while listNode:
            result.insert(0, listNode.val)
            listNode = listNode.next
        return result
```

