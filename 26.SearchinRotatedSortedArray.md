##### Problem

Suppose an array sorted in ascending order is rotated at some pivot unknown to you beforehand.

(i.e., `[0,1,2,4,5,6,7]` might become `[4,5,6,7,0,1,2]`).

You are given a target value to search. If found in the array return its index, otherwise return -1.

You may assume no duplicate exists in the array.

Your algorithm's runtime complexity must be in the order of `O(log n)`.

###### Example
```
Input: nums = [4,5,6,7,0,1,2], target = 0
Output: 4
```

###### Example
```
Input: nums = [4,5,6,7,0,1,2], target = 3
Output: -1
```
##### Solution
```
class Solution:
    def search(self, a, target):
        length = len(a)
        low = 0
        high = length - 1
        while low < high:
            mid = int((low + high) / 2)
            if a[mid] > a[high]:
                low = mid + 1
            else:
                high = mid
        rot = low
        low = 0
        high = length - 1
        while low <= high:
            mid = int((low + high) / 2)
            real_mid = (mid + rot) % length
            if a[real_mid] == target:
                return real_mid
            if a[real_mid] < target:
                low = mid + 1
            else:
                high = mid - 1
        return -1
```

