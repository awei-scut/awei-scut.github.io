---
title: leetcode-1023
date: 2019-04-09 16:35:57
tags:
categories: leetcode
---

### Camelcase Matching 

A query word matches a given `pattern` if we can insert **lowercase** letters to the pattern word so that it equals the `query`. (We may insert each character at any position, and may insert 0 characters.)

Given a list of `queries`, and a `pattern`, return an `answer` list of booleans, where `answer[i]` is true if and only if `queries[i]` matches the `pattern`.

<!-- more -->

### example

```
Input: queries = ["FooBar","FooBarTest","FootBall","FrameBuffer","ForceFeedBack"], pattern = "FB"
Output: [true,false,true,true,false]
Explanation: 
"FooBar" can be generated like this "F" + "oo" + "B" + "ar".
"FootBall" can be generated like this "F" + "oot" + "B" + "all".
"FrameBuffer" can be generated like this "F" + "rame" + "B" + "uffer".
```

### 思路

题目的意思就是说pattern通过加小写字母之后，能否形成query字符串。

对query做一次遍历，如果当前字符是小写的，pattern中可有可无。而如果是大写的，则字符串必须有此字符，否则返回false

### 代码

```c++
class Solution {
public:
    vector<bool> camelMatch(vector<string>& queries, string pattern) {
        vector<bool> res;
        int len = queries.size();
        for(int i = 0 ; i < len; i++){
            res.push_back(ifmatch(queries[i], pattern));
        }
        return res;
    }
    bool ifmatch(string & a, string & p){
        int m = a.length();
        int n = p.length();
        //record用来记录当前patter字符的位置
        int record = 0;;
        for(int j = 0; j< m; j++){
            if(islower(a[j]) && a[j] == p[record]){
                record ++;
                continue;
            }
            if(islower(a[j]) && a[j] != p[record]) continue;
                
            if(record == n) return false;
            if(isupper(a[j]) && a[j] == p[record]){
                record++;
                continue;
            }
            if(isupper(a[j]) && a[j] != p[record]) return false;
        }
        return record == n?true:false;
    }
};
```



