---
title: 剑指offer-8
date: 2019-04-01 09:52:47
tags:
categories: 剑指offer
---

#### 题目描述

把一个数组最开始的若干个元素搬到数组的末尾，我们称之为数组的旋转。 输入一个非减排序的数组的一个旋转，输出旋转数组的最小元素。 例如数组{3,4,5,1,2}为{1,2,3,4,5}的一个旋转，该数组的最小值为1。 NOTE：给出的所有元素都大于0，若数组大小为0，请返回0。 

<!-- more -->

#### 解析

因为原序列为非递减序列，所以旋转后的序列，在错开的那个点处值会突然降低，或者相等。突然降低的那个值则为最小值。对于序列都相等的情况，只需返回任意一个值即可。

#### 代码

coded by c++

```c++
class Solution {
public:
    int minNumberInRotateArray(vector<int> rotateArray) {
        if(rotateArray.size() == 0){
            return 0;
        }
        for(int i = 0;i < rotateArray.size()-1;i++){
            if(rotateArray[i] > rotateArray[i+1])
                return rotateArray[i+1];
        }
        return rotateArray[0];
    }
};
```

