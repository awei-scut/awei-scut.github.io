---
title: 剑指offer题-2
date: 2019-03-28 23:13:54
tags: 递归
categories: 剑指offer
---

#### 题目描述

一只青蛙一次可以跳上1级台阶，也可以跳上2级。求该青蛙跳上一个n级的台阶总共有多少种跳法（先后次序不同算不同的结果）。 

时间限制：1秒 空间限制：32768K 

<!-- more -->

#### 思路

这道题和斐波那契数列那道类似的，也是很简单。这里采用递归来解决。(偷个懒不用动态规划的思想)。

哎，其实从底部往上加也不难..有兴趣的可以建议实现一下

#### 解答

```c++
class Solution {
public:
    int jumpFloor(int number) {
        if(number == 1)
            return 1;
        if(number == 2)
            return 2;
        return jumpFloor(number-1) + jumpFloor(number-2);
    }
};
```

