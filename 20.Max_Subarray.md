#### Maximum Subarray

问题描述

* Find the contiguous subarray within an array (containing at least one number) which has the largest sum.

* For example, given the array `[-2,1,-3,4,-1,2,1,-5,4]`,
the contiguous subarray `[4,-1,2,1]` has the largest `sum = 6`.

```
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

超时代码，可以得到结果但是oj超时
```
       
       block = 1
        sum_array = sum(nums)
        while block <= len(nums):
          for i in range(len(nums)):
            tmp_array = nums[i:i + block]
            tmp_sum = sum(tmp_array)
            if tmp_sum > sum_array:
                sum_array = tmp_sum

          block = block + 1
        return sum_array
```
