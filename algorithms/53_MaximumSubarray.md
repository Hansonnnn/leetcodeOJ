## Problem

Given an integer array nums, find the contiguous subarray (containing at least one number) which has the largest sum and return its sum.

**Example:**
```
Input: [-2,1,-3,4,-1,2,1,-5,4],
Output: 6
Explanation: [4,-1,2,1] has the largest sum = 6.
```

## Solution
```python
class Solution(object):
    def maxSubArray(self, nums):
        """
        :type nums: List[int]
        :rtype: int
        """
        if len(nums) == 0:
            return 0
        sum_array = nums[0]
        max_sum = sum_array
        for num in nums[1:]:
            sum_array = max(num, sum_array + num)
            max_sum = max(max_sum, sum_array)
        return max_sum
```
以上结果不是最优解，待优化。
```
Runtime: 52 ms, faster than 28.84% of Python online submissions for Maximum Subarray.
Memory Usage: 12.1 MB, less than 5.10% of Python online submissions for Maximum Subarray.
```
link: https://leetcode.com/problems/maximum-subarray/submissions/

