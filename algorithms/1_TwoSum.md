## Problem

Given an array of integers, return indices of the two numbers such that they add up to a specific target.

You may assume that each input would have exactly one solution, and you may not use the same element twice.

Example:
```
Given nums = [2, 7, 11, 15], target = 9,

Because nums[0] + nums[1] = 2 + 7 = 9,
return [0, 1].
```

## Solution
```
public int[] twoSum(int[] nums, int target) {
    int[] res=new int[2];
    int len=nums.length;
    for(int i=0;i<len;i++)
      for(int j=len-1;j<len&&j>=0;j--)
    {
        if(nums[i]+nums[j]==target&&i!=j) {
            res[0]=i;
            res[1]=j;
            break;
        }
    }
      return res;
}
```
## Solution 2
```python
class Solution:
    def twoSum(self, nums, target):
        kv = {}
        for i in range(len(nums)):
            another = target - nums[i]
            if another in kv:
                return [kv[another], i]
            kv[nums[i]] = i
```
link: https://leetcode.com/problems/two-sum/

