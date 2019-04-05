## Problem

Given a string containing just the characters '(', ')', '{', '}', '[' and ']', determine if the input string is valid.

An input string is valid if:

Open brackets must be closed by the same type of brackets.
Open brackets must be closed in the correct order.
Note that an empty string is also considered valid.

**Example 1:**
```
Input: "()"
Output: true
```
**Example 2:**
```
Input: "()[]{}"
Output: true
```
**Example 3:**
```
Input: "(]"
Output: false
```
**Example 4:**
```
Input: "([)]"
Output: false
```
**Example 5:**
```
Input: "{[]}"
Output: true
```

## Solution
```
class Solution:
    def isValid(self, str1):
        stack = []
        mapping = {")": "(", "}": "{", "]": "["}
        for s in str1:
            if s in mapping:
                top_elements = stack.pop() if stack else '_'
                if mapping[s] != top_elements:
                    return False
            else:
                stack.append(s)
        return not stack
```

link: https://leetcode.com/problems/valid-parentheses/


