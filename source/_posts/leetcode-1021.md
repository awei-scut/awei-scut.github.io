---
title: leetcode-1021
date: 2019-04-09 16:23:12
tags:
categories: leetcode
---

### Remove Outermost Parentheses 

A valid parentheses string is either empty `("")`, `"(" + A + ")"`, or `A + B`, where `A` and `B` are valid parentheses strings, and `+` represents string concatenation.  For example, `""`, `"()"`, `"(())()"`, and `"(()(()))"` are all valid parentheses strings.

A valid parentheses string `S` is **primitive** if it is nonempty, and there does not exist a way to split it into `S = A+B`, with `A` and `B` nonempty valid parentheses strings.

<!-- more -->

Given a valid parentheses string `S`, consider its primitive decomposition: `S = P_1 + P_2 + ... + P_k`, where `P_i` are primitive valid parentheses strings.

Return `S` after removing the outermost parentheses of every primitive string in the primitive decomposition of `S`.

题目说了一大堆，其实意思就是说给定一段由括号组成的字符串，返回的是将它的最外层那一对去掉。

### 思路

设置一个变量n初始值为0

当n == 0的，就不加入res字符串，左括号就n+1,右括号就n-1

持续下去，到最后n=0就是最外层的右括号，也不加进去，所以就结束了

时间为o(n)

###代码

code by c++

```c++
class Solution {
public:
    string removeOuterParentheses(string S) {
        string res = "";
        int n = 0;
        for(int i = 0; i < S.length(); i++){
            if(S[i] == '(' && n++) res += S[i];
            if(S[i] == ')' && --n) res += S[i];
        }
        return res;
    }
};
```

