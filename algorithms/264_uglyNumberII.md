## Problem

Write a program to find the `n-th` ugly number.

Ugly numbers are positive numbers whose prime factors only include `2, 3, 5`. 

**Example:**
```
Input: n = 10
Output: 12
Explanation: 1, 2, 3, 4, 5, 6, 8, 9, 10, 12 is the sequence of the first 10 ugly numbers.
```
**Note:**

- 1 is typically treated as an ugly number.
- n does not exceed 1690.

**description**

DP动态规划

## Solution

```python
class Solution:
    def nthUglyNumber(self, n):
        """
        :type n: int
        :rtype: int
        """
        if n == 0: return 0
        if n == 1: return 1
        result = [0] * n
        result[0] = 1
        t2 = t3 = t5 = 0
        for i in range(1, n):
            result[i] = min([result[t2] * 2, result[t3] * 3, result[t5] * 5])
            if result[i] == result[t2] * 2: t2 += 1
            if result[i] == result[t3] * 3: t3 += 1
            if result[i] == result[t5] * 5: t5 += 1
        return result[n - 1]
```

link:https://leetcode.com/problems/ugly-number-ii/

