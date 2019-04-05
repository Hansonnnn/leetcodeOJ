## Problem

Given a set of candidate numbers (candidates) (without duplicates) and a target number (target), find all unique combinations in candidates where the candidate numbers sums to target.

The same repeated number may be chosen from candidates unlimited number of times.

**Note**
* All numbers (including target) will be positive integers.
* The solution set must not contain duplicate combinations.

**Example1**:
```
Input: candidates = [2,3,6,7], target = 7,
A solution set is:
[
  [7],
  [2,2,3]
]
```
**Example2**:
```
Input: candidates = [2,3,5], target = 8,
A solution set is:
[
  [2,2,2,2],
  [2,3,3],
  [3,5]
]
```

## Solution

```
class Solution:
    def combinationSum(self, candidates, target):
        res = []
        path = []
        index = 0
        self.dfs_travel(candidates, target, index, path, res)
        return res

    def dfs_travel(self, nums, target, index, path, res):
        if target < 0:
            return
        if target == 0:
            res.append(path)
            return
        for i in range(index, len(nums)):
            self.dfs_travel(nums, target - nums[i], i, path + [nums[i]], res)
```

link: https://leetcode.com/problems/combination-sum/

