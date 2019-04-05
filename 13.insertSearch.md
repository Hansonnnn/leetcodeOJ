### insertSearch

* Question

```
Given a sorted array and a target value, return the index if the target is found. If not, return the index where it would be if it were inserted in order.

You may assume no duplicates in the array.

Here are few examples.
[1,3,5,6], 5 → 2
[1,3,5,6], 2 → 1
[1,3,5,6], 7 → 4
[1,3,5,6], 0 → 0

```
给定一个有序列表，并给出另外一个元素，在这个有序列表当中寻找是否存在这个元素，如果存在即返回其索引，如果不存在请给出它应该在此列表的哪个索引处。

* 思路

这道题的关键字眼在于“有序”，处理有序列表首先可以想到效率还不错的二分搜索（O(logn)）。而二分搜索有递归与非递归两种实现，在这里使用非递归实现。

```
    def searchInsert(self,nums,target):
        start = 0
        end = len(nums)-1
        while end >= start:
            mid = (end-start)//2 + start
            if(nums[mid] == target):
                return mid
            if(nums[mid] > target):
                end = mid - 1
            else:
                start = mid + 1
        return start

```
