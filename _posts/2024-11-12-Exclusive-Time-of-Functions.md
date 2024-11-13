---
layout:     post
title:      LeetCode 636 Exclusive Time of Functions (Python)
number:     636
level:      Medium
lcurl:      exclusive-time-of-functions
youtube:    
bilibili1:  
xigua:      
date:       2024-11-12
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - Stack
---

### 题目

On a single-threaded CPU, we execute a program containing n functions. Each function has a unique ID between 0 and n-1.

Function calls are stored in a call stack: when a function call starts, its ID is pushed onto the stack, and when a function call ends, its ID is popped off the stack. The function whose ID is at the top of the stack is the current function being executed. Each time a function starts or ends, we write a log with the ID, whether it started or ended, and the timestamp.

You are given a list logs, where logs[i] represents the ith log message formatted as a string "{function_id}:{"start" | "end"}:{timestamp}". For example, "0:start:3" means a function call with function ID 0 started at the beginning of timestamp 3, and "1:end:2" means a function call with function ID 1 ended at the end of timestamp 2. Note that a function can be called multiple times, possibly recursively.

A function's exclusive time is the sum of execution times for all function calls in the program. For example, if a function is called twice, one call executing for 2 time units and another call executing for 1 time unit, the exclusive time is 2 + 1 = 3.

Return the exclusive time of each function in an array, where the value at the ith index represents the exclusive time for the function with ID i.

### 解题思路

用一个数组维护每个进程的运行时间，维护一个栈并记录前一个遇到的时间点，遇到start给栈顶元素增加时间，并把当前线程进栈，遇到end，出栈并给给其计算时间。

### 代码
```python
class Solution:
    def exclusiveTime(self, n: int, logs: List[str]) -> List[int]:
        res = [0] * n
        s = []
        pre = 0
        for log in logs:
            fid, status, ts = log.split(":")
            fid, ts = int(fid), int(ts)
            if status == "start":
                if s:
                    res[s[-1]] += ts - pre
                s.append(fid)
                pre = ts
            else:
                res[s.pop()] += ts - pre + 1
                pre = ts + 1
        return res
```
