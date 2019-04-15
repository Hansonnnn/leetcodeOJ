## Problem

Write an efficient algorithm that searches for a value in an `m x n` matrix. This matrix has the following properties:
- Integers in each row are sorted from left to right.
- The first integer of each row is greater than the last integer of the previous row.

**Example1**
```
Input:
matrix = [
  [1,   3,  5,  7],
  [10, 11, 16, 20],
  [23, 30, 34, 50]
]
target = 3
Output: true
```

**Example2**
```
Input:
matrix = [
  [1,   3,  5,  7],
  [10, 11, 16, 20],
  [23, 30, 34, 50]
]
target = 13
Output: false
```

## Solution 

**Description**

这道题第一种解法来自于两个指针，因为题目已经给出该矩阵是一个已排序的矩阵，所以放两个指针i和j，j在矩阵右上方，i在左上方。移动的时候自右至左移动j指针保持i不动，依次比较所指元素与target的，如果所指元素大于target，那么将j前移，否则i后移，如果所指元素与target相等即返回True，否则继续遍历，直至遍历完毕矩阵。

```python
class Solution:
    def searchMatrix(self, matrix, target):
        if not matrix: return
        m = len(matrix)
        n = len(matrix[0])
        j = n - 1
        i = 0
        while j >= 0 and i < m:
            if matrix[i][j] > target:
                j -= 1
            elif matrix[i][j] < target:
                i += 1
            elif matrix[i][j] == target:
                return True
        return False
```

## Solution2

**二分搜索解法**

```python
class Solution:
    def searchMatrix(self, matrix: List[List[int]], target: int) -> bool:
        m = len(matrix)
        if m == 0:
            return False
        n = len(matrix[0])
        
        # binary search
        left, right = 0, m * n - 1
        while left <= right:
                pivot_idx = (left + right) // 2
                pivot_element = matrix[pivot_idx // n][pivot_idx % n]
                if target == pivot_element:
                    return True
                else:
                    if target < pivot_element:
                        right = pivot_idx - 1
                    else:
                        left = pivot_idx + 1
        return False
```

link:https://leetcode.com/problems/search-a-2d-matrix/
