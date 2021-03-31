---
layout:     post
title:      LeetCode 936 Stamping The Sequence (Python)
number:     936
level:      Hard
lcurl:      stamping-the-sequence
youtube:    LD8FfUYVCSY
bilibili1:  //player.bilibili.com/player.html?aid=757250501&bvid=BV1d64y1D7fq&cid=317691301&page=1
xigua:      
date:       2021-03-31
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - 
---

### 题目

You want to form a target string of lowercase letters.

At the beginning, your sequence is target.length '?' marks.  You also have a stamp of lowercase letters.

On each turn, you may place the stamp over the sequence, and replace every letter in the sequence with the corresponding letter from the stamp.  You can make up to 10 * target.length turns.

For example, if the initial sequence is "?????", and your stamp is "abc",  then you may make "abc??", "?abc?", "??abc" in the first turn.  (Note that the stamp must be fully contained in the boundaries of the sequence in order to stamp.)

If the sequence is possible to stamp, then return an array of the index of the left-most letter being stamped at each turn.  If the sequence is not possible to stamp, return an empty array.

For example, if the sequence is "ababc", and the stamp is "abc", then we could return the answer [0, 2], corresponding to the moves "?????" -> "abc??" -> "ababc".

Also, if the sequence is possible to stamp, it is guaranteed it is possible to stamp within 10 * target.length moves.  Any answers specifying more than this number of moves will not be accepted.

### 解题思路

把过程反序，从target盖成问号，每次找到一个能盖的地方盖，并把盖到的地方都变成问号了，如果发现无法盖了，返回空，都变成问号了返回结果

### 代码
```python
class Solution:
    def movesToStamp(self, stamp: str, target: str) -> List[int]:
        def check(word):
            ret = 0
            for i in range(m):
                if word[i] == '?':
                    continue
                if word[i] == stamp[i]:
                    ret += 1
                else:
                    return 0
            return ret
        
        target = list(target)
        m, n = len(stamp), len(target)
        tot, res = 0, []
        while tot < n:
            tmp = tot
            for i in range(n - m + 1):
                cur = check(target[i: i + m])
                if cur:
                    tot += cur
                    target[i: i + m] = ['?'] * m
                    res.append(i)
            if tmp == tot:
                return []
        return res[::-1]
```
