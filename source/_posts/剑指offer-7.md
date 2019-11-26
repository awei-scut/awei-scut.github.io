---
title: 剑指offer-7
date: 2019-04-01 09:47:49
tags: 堆栈
categories: 剑指offer
---

#### 题目描述

用两个栈来实现一个队列，完成队列的Push和Pop操作。 队列中的元素为int类型。 

<!-- more -->

#### 解析

队列每次push,都往stack1推即可，并且做出判断，当stack2为空时，则将stack2的元素全部到stack1。而当队列每次pop时，应从stack2 pop出元素，并且做出判断，当stack2为空时，则检查stack1中是否有剩余元素，若有则pop到stack2，再把stack2的顶层元素pop出去即可。

#### 代码

coded by python

```python
# -*- coding:utf-8 -*-
class Solution:
    def __init__(self):
        self.stack1 = []
        self.stack2 = []
    def push(self, node):
        # write code here
        
        self.stack1.append(node)
        if self.stack2 == []:
            for i in range(len(self.stack1)):
                self.stack2.append(self.stack1.pop())

    def pop(self):
        # return xx
        if self.stack2 !=[]:
            return self.stack2.pop()
        elif self.stack1 != []:
            for i in range(len(self.stack1)):
                self.stack2.append(self.stack1.pop())
            return self.stack2.pop()
        
```

