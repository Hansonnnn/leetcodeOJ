## Problem

Given a string containing just the characters `'('` and `')'`, find the length of the longest valid (well-formed) parentheses substring.

**Example 1:**
```
Input: "(()"
Output: 2
Explanation: The longest valid parentheses substring is "()"
```

**Example 2:**
```
Input: ")()())"
Output: 4
Explanation: The longest valid parentheses substring is "()()"
```
**Description**

DP解决

## Solution

```python
class Solution:
    def longestValidParentheses(self, s):
        if not s:
            return 0
        res = [0] * len(s)
        max_res = 0
        for i in range(1, len(s)):
            if s[i] == ')':
                if s[i - 1] == '(':
                    res[i] = (res[i - 2] if i >= 2 else 0) + 2
                elif (i - res[i - 1]) > 0 and s[i - res[i - 1] - 1] == '(':
                    res[i] = res[i - 1] + (res[i - res[i - 1] - 2] if (i - res[i - 1]) >= 2 else 0) + 2
            max_res = max(max_res, res[i])
        return max_res
```

link:https://leetcode.com/problems/longest-valid-parentheses/
