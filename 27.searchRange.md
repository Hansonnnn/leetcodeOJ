##### Problem

Given an array of integers nums sorted in ascending order, find the starting and ending position of a given target value.

Your algorithm's runtime complexity must be in the order of `O(log n)`.

If the target is not found in the array, return `[-1, -1]`.

###### Example1:
```
Input: nums = [5,7,7,8,8,10], target = 8
Output: [3,4]
```

###### Example2:
```
Input: nums = [5,7,7,8,8,10], target = 6
Output: [-1,-1]
```

##### Solution 
```
class Solution:
    def searchRange(self, nums, target):
        res = [-1, -1]
        length = len(nums)

        if length == 0 or nums is None:
            return res
        low = 0
        high = length - 1

        while low < high:
            mid = int((low + high) / 2)
            if nums[mid] < target:
                low = mid + 1
            else:
                high = mid
        if nums[low] != target:
            return res
        else:
            res[0] = low
        high = length - 1
        while low < high:
            mid = int((low + high) / 2) + 1
            if nums[mid] > target:
                high = mid - 1
            else:
                low = mid

        res[1] = high
        return res

