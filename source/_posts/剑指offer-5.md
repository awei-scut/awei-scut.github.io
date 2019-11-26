---
title: 剑指offer-5
date: 2019-04-01 09:37:20
tags: 反转链表
categories: 剑指offer
---

#### 题目描述

输入一个链表，按链表值从尾到头的顺序返回一个ArrayList。

<!-- more -->

#### 解析

这题看着是要打印链表，其实就是把链表反转一下就可以了,非常简单，反转链表操作也很经典也简单，不熟悉的话背一下就OK了。

#### 代码

coded by python

```python
class Solution:
    # 返回从尾部到头部的列表值序列，例如[1,2,3]
    def printListFromTailToHead(self, listNode):
        # write code here
        curr = listNode
        pre = None
        while curr!=None:
            temp = curr.next
            curr.next = pre
            pre = curr
            curr = temp
        res = []
        while pre!=None:
            res.append(pre.val)
            pre = pre.next
        return res
```

- 

