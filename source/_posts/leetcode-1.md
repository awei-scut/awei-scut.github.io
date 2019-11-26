---
title: leetcode-1
date: 2019-03-25 20:52:29
tags: 对撞指针
categories: leetcode
---

##### 题号 1

Given an array of integers, return **indices** of the two numbers such that they add up to a specific target.

You may assume that each input would have **exactly** one solution, and you may not use the *same* element twice.

<!-- more -->

#### example:

```
Given nums = [2, 7, 11, 15], target = 9,

Because nums[0] + nums[1] = 2 + 7 = 9,
return [0, 1].
```

#### code(by python)

```python
class Solution:
    def twoSum(self, nums: List[int], target: int) -> List[int]:
        hash_map = dict()
        for i, x in enumerate(nums):
            if target- x in hash_map:
                return [i, hash_map[target-x]]
            hash_map[x] = i
```

Runtime: 40 ms, faster than 81.67% of Python3 online submissions for Two Sum.

Memory Usage: 14.1 MB, less than 10.76% of Python3 online submissions for Two Sum.