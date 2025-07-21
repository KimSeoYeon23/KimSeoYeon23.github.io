---
layout: post
title:  "Valid Parentheses"
date:   2025-07-21 15:25:00 +0900
categories:
  - Dev
  - codingtest
tag: codingtest
comments: true
---

* this unordered seed list will be replaced by the toc
  {:toc}

## LeetCode Valid Parentheses

### 문제

Given a string s containing just the characters '(', ')', '{', '}', '[' and ']', determine if the input string is valid.

An input string is valid if:

Open brackets must be closed by the same type of brackets.
Open brackets must be closed in the correct order.
Every close bracket has a corresponding open bracket of the same type.


### 예시

Example 1:

Input: s = "()"

Output: true

Example 2:

Input: s = "()[]{}"

Output: true

Example 3:

Input: s = "(]"

Output: false

Example 4:

Input: s = "([])"

Output: true

Example 5:

Input: s = "([)]"

Output: false

## 풀이

```py
class Solution:
  def isValid(self, s: str) -> bool:
    valid = {
      ')': '(',
      '}': '{',
      ']': '['
    }
    stack = []

    for string in s:
      if string in valid.values():
        stack.append(string)
      else:
        if stack and valid[string] == stack[-1]:
          stack.pop()
        else:
          return False
    if stack:
      return False
    return True
```
