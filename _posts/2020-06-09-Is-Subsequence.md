---
layout:     post
title:      LeetCode 392 Is Subsequence (With Follow up) (Python)
number:     392
level:      Easy
lcurl:      is-subsequence
youtube:    5daodUGSFp0
bilibili1:  //player.bilibili.com/player.html?aid=668486003&bvid=BV1Za4y1a73v&cid=200301606&page=1
xigua:      
date:       2020-06-09
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - Binary Search
---

### 题目

Given a string s and a string t, check if s is subsequence of t.

A subsequence of a string is a new string which is formed from the original string by deleting some (can be none) of the characters without disturbing the relative positions of the remaining characters. (ie, "ace" is a subsequence of "abcde" while "aec" is not).

#### Follow up:
If there are lots of incoming S, say S1, S2, ... , Sk where k >= 1B, and you want to check one by one to see if T has its subsequence. In this scenario, how would you change your code?

### 解题思路
1. 使用两个指针指向两个字符串，如果指到相同的字符则一起向后移动，否则只移动t的
2. 将s转换成一个list，遍历t，如果与s中的第一个字母相同则pop s中的第一个字母，如果s最后为空，则是true

#### Follow up:
先预处理，把t的存到一个字典中，key是字母，value是这个字母所有出现的位置，然后对s中的每个字符，在t中这个字母对应的位置进行二分，这里要维护每次二分到的位置，后面的字符必须要在这个位置之后才能被使用

### 代码
```python
class Solution:
    def isSubsequence(self, s: str, t: str) -> bool:
        pt = -1
        for c in s:
            while pt < len(t) - 1:
                pt += 1
                if c == t[pt]:
                    break
            else:
                return False
        return True
```
```python
class Solution:
    def isSubsequence(self, s: str, t: str) -> bool:
        q = list(q)
        for c in t:
            if not q: return True
            if c == q[0]:
                q.pop(0)
        return not q
```
#### Follow up:
```python
class Solution:
    def isSubsequence(self, s: str, t: str) -> bool:
        dic = collections.defaultdict(list)
        for i, c in enumerate(t):
            dic[c].append(i)
        
        cur = -1
        for c in s:
            if c not in dic:
                return False
            l = dic[c]
            p = bisect.bisect_left(l, cur)
            if p == len(l):
                return False
            cur = l[p] + 1
        return True
```
