---
title: 剑指offer-3
date: 2019-04-01 09:29:24
tags: 查找问题
categories: 剑指offer
---

#### 题目描述

在一个二维数组中（每个一维数组的长度相同），每一行都按照从左到右递增的顺序排序，每一列都按照从上到下递增的顺序排序。请完成一个函数，输入这样的一个二维数组和一个整数，判断数组中是否含有该整数。 

#### 解析

由于数组行与列都是递增，因此可以直接查找(用一个循环逐个查找)，并剪掉一些不可能的可能。有点类似与剪纸的思想，但是时间复杂度在最坏的情况下也可能是O(n^2)

#### 代码

code by c++

```c++
class Solution {
public:
    bool Find(int target, vector<vector<int> > array) {
        int m = array.size();
        int n = array[0].size();
        
        for(int i=0;i< m ;i++){
            for(int j=0;j<n;j++){
            if(array[i][j]==target){
                return true;
            }else if(array[i][j]>target){
                break;
            }
        }
        }
        return false;
    }
};
```

