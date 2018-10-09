---
title: 链表-链表中倒数第k个结点
toc: true
date: 2018-09-21 11:31:34
tags: 链表
categories: 剑指offer
---

# 题目

输入一个链表，输出该链表中倒数第k个结点。

[题目链接](https://www.nowcoder.com/practice/529d3ae5a407492994ad2a246518148a?tpId=13&tqId=11167&tPage=1&rp=1&ru=%2Fta%2Fcoding-interviews&qru=%2Fta%2Fcoding-interviews%2Fquestion-ranking)

# 思路

我们可以定义两个指针。第一个指针从链表的头指针开始遍历向前走k-1，第二个指针保持不动；从第k步开始，第二个指针也开始从链表的头指针开始遍历。由于两个指针的距离保持在k-1，当第一个（走在前面的）指针到达链表的尾结点时，第二个指针（走在后面的）指针正好是倒数第k个结点。

![åæOfferï¼ååï¼ï¼é¾è¡¨ä¸­åæ°ç¬¬kä¸ªç"ç¹](https://ws1.sinaimg.cn/large/006tNbRwgy1fvh09o15xjj30hb08bdg1.jpg)

# 代码

```python
# -*- coding:utf-8 -*-
# class ListNode:
#     def __init__(self, x):
#         self.val = x
#         self.next = None
 
class Solution:
    def FindKthToTail(self, head, k):
        # write code here
        if head == None or k == 0:
            return None
        phead = head
        pbehind = head
        for i in range(k-1):
            if phead.next == None:
                return None
            else:
                phead = phead.next
        while phead.next != None:
            phead = phead.next
            pbehind = pbehind.next
        return pbehind
```

