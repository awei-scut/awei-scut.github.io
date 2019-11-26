---
title: leetcode-287
date: 2019-03-27 12:30:44
tags: 
categories: leetcode
---

### leetcode 287

早上随便找了道题，tag是two pointer,但是做的时候却没想到怎么解.. 换了其它的办法

题目是要求不改变原数组的，代码里改变了... (之后再看看其它解法吧！)

<!-- more -->

### 描述

Given an array *nums* containing *n* + 1 integers where each integer is between 1 and *n* (inclusive), prove that at least one duplicate number must exist. Assume that there is only one duplicate number, find the duplicate one. 

### Example

```
Input: [1,3,4,2,2]
Output: 2
```

code by c++:

```c++
class Solution {
public:
    int findDuplicate(vector<int>& nums) {
        int i=0;
        int j=nums.size();
        sort(nums.begin(), nums.end());
        for( int k = 1; k < nums.size();k++){
            if(nums[k] == nums[k-1])
                return nums[k];
        }
        return -1;
    }
};
```

### 思路

先对vector 进行排序，排序之后相邻位置一直比较，如果发现重复，就说明找到了重复的这个值。