---
title: 剑指offer-6
date: 2019-04-01 09:40:14
tags: -重建二叉树
      -递归
categories: 剑指offer
---

#### 题目描述

输入某二叉树的前序遍历和中序遍历的结果，请重建出该二叉树。假设输入的前序遍历和中序遍历的结果中都不含重复的数字。例如输入前序遍历序列{1,2,4,7,3,5,6,8}和中序遍历序列{4,7,2,1,5,3,8,6}，则重建二叉树并返回。 

<!-- more -->

#### 解析

这个题我采取了递归的做法，因此每次要将前序遍历序列和中序遍历序列分为三部分，即根节点、左子树、右子树。然后左右子树再调用函数递归。我创建了四个vector用于存放左子树(右子树)的前序遍历和后序遍历序列，之后调用函数递归。

#### 代码

coded by c++

```c++
class Solution {
public:
    TreeNode* reConstructBinaryTree(vector<int> pre,vector<int> vin) {
        if(pre.size() == 0 && vin.size() == 0 )
            return NULL;
        if(pre.size() == 1 && vin.size() == 1){
            TreeNode* p = new TreeNode(pre[0]);
            return p;
        }      
        TreeNode* ret = new TreeNode(pre[0]);
        auto index = distance(vin.begin(),find(vin.begin(), vin.end(), pre[0]));
        vector<int> pre1(0);
        vector<int> pre2(0);
        vector<int> vin1(0);
        vector<int> vin2(0);
        if(pre.begin()+1 != (pre.begin() + 1 +index)){
            pre1.assign(pre.begin()+1, pre.begin()+ 1 + index);
        }
        if((pre.begin()+1+ index)!= pre.end())
            pre2.assign(pre.begin()+1+ index, pre.end());
        if(vin.begin()!=(vin.begin()+index ))
            vin1.assign(vin.begin(),vin.begin()+index );
        if((vin.begin()+index + 1)!= vin.end())
            vin2.assign(vin.begin()+index + 1, vin.end()); 
        ret->left = reConstructBinaryTree(pre1, vin1);
        ret->right = reConstructBinaryTree(pre2, vin2);
        return ret;
    }
};
```

#### 注意

采用递归思想，每次函数要注意的是递归终止条件，否则很容易陷入死循环。