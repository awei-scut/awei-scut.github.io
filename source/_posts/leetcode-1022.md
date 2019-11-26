---
title: leetcode-1022
date: 2019-04-09 16:28:00
tags:
categories: leetcode
---

###  Sum of Root To Leaf Binary Numbers 

description: Given a binary tree, each node has value `0` or `1`.  Each root-to-leaf path represents a binary number starting with the most significant bit.  For example, if the path is `0 -> 1 -> 1 -> 0 -> 1`, then this could represent `01101` in binary, which is `13`.

For all leaves in the tree, consider the numbers represented by the path from the root to that leaf.

Return the sum of these numbers.

<!-- more -->

### example

![image](https://user-images.githubusercontent.com/29776707/55785314-c8d5aa00-5ae4-11e9-95e4-6df227414fd7.png)

```
Input: [1,0,1,0,1,0,1]
Output: 22
Explanation: (100) + (101) + (110) + (111) = 4 + 5 + 6 + 7 = 22
```

给一颗树，值为0或者1 

求出所有根节点到叶结点的所有路径的二进制表示的和。

### 思路

这道题主要要考虑一个数的范围，因为可能数据会特别大。所以要做一个取余的操作，不然会导致溢出。

至于路径和就很简单了，递归调用，每次都传入一个根结点到当前结点的和。

### 代码

```c++
class Solution {
public:
    int sumRootToLeaf(TreeNode* root) {    
        if(!root)
            return 0;
        return sum(root, 0);
    }
    int sum(TreeNode* root, int s){
        if(!root) return 0;
        const int k = pow(2,31);
        s = ((s << 1) | root->val) % k;
        if(!root->left && !root->right)
            return s;
        return sum(root->left, s)+
                sum(root->right, s);
    }
};
```



