---
layout:     post
title:      LeetCode 71 Simplify Path (Python)
number:     71
level:      Medium
lcurl:      simplify-path
youtube:    oIMoMEnxpsE
bilibili1:  //player.bilibili.com/player.html?aid=459006516&bvid=BV1D5411J72c&cid=293198209&page=1
xigua:      
date:       2021-02-05
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - Stack
---

### 题目

Given a string path, which is an absolute path (starting with a slash '/') to a file or directory in a Unix-style file system, convert it to the simplified canonical path.

In a Unix-style file system, a period '.' refers to the current directory, a double period '..' refers to the directory up a level, and any multiple consecutive slashes (i.e. '//') are treated as a single slash '/'. For this problem, any other format of periods such as '...' are treated as file/directory names.

The canonical path should have the following format:

- The path starts with a single slash '/'.
- Any two directories are separated by a single slash '/'.
- The path does not end with a trailing '/'.
- The path only contains the directories on the path from the root directory to the target file or directory (i.e., no period '.' or double period '..')
Return the simplified canonical path.

### 解题思路

用`/`分开，用栈存没给部分，如果是`.`或者是空，继续，`..`pop，最后再用`/`join起来

### 代码
```python
class Solution:
    def simplifyPath(self, path: str) -> str:
        res = []
        for it in path.rstrip('/').split('/'):
            if it == '.' or it == "":
                continue
            elif it == "..":
                if len(res) > 0:
                    res.pop()
            else:
                res.append(it)
        return '/' + '/'.join(res)
```
