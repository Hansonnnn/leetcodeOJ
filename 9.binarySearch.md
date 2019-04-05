### 二分搜索

代码包括二分搜索递归及非递归实现

递归实现

```
# -*- coding:utf-8 -*-
""""二分搜索"""
class Solution(object):
    def searchInsert(self,nums,target):
        length = len(nums)
        if length == 0 or nums == None:
            return 0
        return self.binarySearch(nums,target,0,length-1)
    def binarySearch(self,nums,target,start,end):
        # 设置二分标志位
        flag = ((end-start) // 2) + start
        if nums[flag] == target:
            return flag
        elif nums[flag] > target:
            return self.binarySearch(nums,target,start,flag-1)
        elif nums[flag] < target:
            return self.binarySearch(nums,target,flag+1,end)
        return -1
```

非递归实现

```
    def binarySearch(self,nums,target):
        length =len(nums)
        start =0
        end = length -1
        while end >= start:
         flag = (end-start) // 2 + start
         if(nums[flag] > target):
            end = flag - 1
         elif(nums[flag] < target):
            start = flag + 1
         else:
            return flag
        return -1
