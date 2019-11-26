---
title: 剑指offer-4
date: 2019-04-01 09:33:23
tags: 
categories: 剑指offer
---

#### 题目描述

请实现一个函数，将一个字符串中的每个空格替换成“%20”。例如，当字符串为We Are Happy.则经过替换之后的字符串为We%20Are%20Happy。

<!-- more -->

#### 解析

这个题的难点主要在于替换的字符串多于1个，因此不能直接替换，否则会将后面的字符串覆盖掉。有两种解法:一种是将空格后的字符串往后移再替换，避免覆盖。另一种是直接开辟新的空间来存储，这里使用python来解决会方便一些。

#### 代码

coded by python

```python
class Solution:
    # s 源字符串
    def replaceSpace(self, s):
        # write code here
        l = len(s)
        t = ""
        for i in range(len(s)):
            if s[i] == " ":
                t = t + "%20"
            else:
                t = t + s[i]
         
        return t
```

