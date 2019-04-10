## Problem
A robot is located at the top-left corner of a `m x n` grid (marked `'Start'` in the diagram below).

The robot can only move either down or right at any point in time. The robot is trying to reach the bottom-right corner of the grid (marked `'Finish'` in the diagram below).

How many possible unique paths are there?

**Note:** m and n will be at most 100.

**Example 1:**
```
Input: m = 3, n = 2
Output: 3
Explanation:
From the top-left corner, there are a total of 3 ways to reach the bottom-right corner:
1. Right -> Right -> Down
2. Right -> Down -> Right
3. Down -> Right -> Right
```

**Example2:** 
```
Input: m = 7, n = 3
Output: 28

```

**Decription**

DP（动态规划）问题

## Solution

```python
class Solution:

    def uniquePaths(self, m, n):
        matrix = [[0 for _ in range(n)] for _ in range(m)]
        i = j = 0
        while i < m:
            while j < n:
                if i == 0 or j == 0:
                    matrix[i][j] = 1
                else:
                    matrix[i][j] = matrix[i][j - 1] + matrix[i - 1][j]
                j += 1
            i += 1
            j = 0
        return matrix[m - 1][n - 1]

```
link:https://leetcode.com/problems/unique-paths/

