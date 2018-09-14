---
title: 剑指offer-合并两个排序的链表
toc: true
date: 2018-09-09 16:21:02
tags: 链表
categories: 剑指offer
---

# 题目

输入两个单调递增的链表，输出两个链表合成后的链表，当然我们需要合成后的链表满足单调不减规则。

[题目链接](https://www.nowcoder.com/practice/d8b6b4358f774294a89de2a6ac4d9337?tpId=13&tqId=11169&tPage=1&rp=1&ru=/ta/coding-interviews&qru=/ta/coding-interviews/question-ranking)

# 思路

随便新建一个结点，可以作为新链表的头结点。输出头结点的next即可。

归并循环条件为两个链表都不为空，注意新链表和旧链表向后移动指针。

# 代码

**python代码**

```python
# -*- coding:utf-8 -*-
# class ListNode:
#     def __init__(self, x):
#         self.val = x
#         self.next = None

class Solution:
    # 返回合并后列表
    def Merge(self, pHead1, pHead2):
        # write code here
        pHead = ListNode(0)
        p = pHead
        
        while pHead1 and pHead2:
            if pHead1.val <= pHead2.val:
                p.next = pHead1
                pHead1 = pHead1.next
            else:
                p.next = pHead2
                pHead2 = pHead2.next
            p = p.next
        
        if pHead1:
            p.next = pHead1
        if pHead2:
            p.next = pHead2
        
        return pHead.next
```



