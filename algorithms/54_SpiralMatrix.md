## Problem
Given a matrix of `m x n` elements (`m` rows, `n` columns), return all elements of the matrix in spiral order.

**Example 1:**
```
Input:
[
 [ 1, 2, 3 ],
 [ 4, 5, 6 ],
 [ 7, 8, 9 ]
]
Output: [1,2,3,6,9,8,7,4,5]
```
**Example 2:**
```
Input:
[
  [1, 2, 3, 4],
  [5, 6, 7, 8],
  [9,10,11,12]
]
Output: [1,2,3,4,8,12,11,10,9,5,6,7]
```
**Description:**

这是一题leetcode中中等难度的题目，题目的题意就是说将矩阵按顺时针螺旋输出。假设有数组`R`行，`C`列，两维数组，当前下标为`(r,c)`，下一步移动至`(cr,cc)`，另外有辅助数组`di`辅助计算下一步下标移动位置。根据归纳可以得：行下标移动辅助数组`(dr)`为`[0,1,0,-1]`，列下标移动辅助数组（`dc`）为`[1,0,-1,0]`。

## Solution

```python
class Solution(object):
    def spiralOrder(self, matrix):
        """
        :type matrix: List[List[int]]
        :rtype: List[int]
        """
        if not matrix: return
        R, C = len(matrix), len(matrix[0])
        seen = [[False] * C for _ in matrix]
        ans = []
        dr = [0, 1, 0, -1]
        dc = [1, 0, -1, 0]
        r = c = di = 0
        for _ in range(R * C):
            ans.append(matrix[r][c])
            seen[r][c] = True
            cr, cc = r + dr[di], c + dc[di]
            if 0 <= cr < R and 0 <= cc < C and not seen[cr][cc]:
                r, c = cr, cc
            else:
                di = (di + 1) % 4
                r, c = r + dr[di], c + dc[di]
        return ans


s = Solution()
print(s.spiralOrder([[1, 2, 3, 4], [5, 6, 7, 8], [9, 10, 11, 12]]))

```
link:https://leetcode.com/problems/spiral-matrix/

时间复杂度：`O(N)`
