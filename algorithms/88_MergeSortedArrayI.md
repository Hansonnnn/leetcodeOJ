## Problem

合并两个有序数组

##### Example:
```
 input:[1,2,3]
       [1,2,2]
 output:[1, 1, 2, 2, 2, 3]
```

##### Solution
```
class Solution:
    def merge(self, nums1, nums2):
        n1 = len(nums1)
        n2 = len(nums2)
        i = 0
        j = 0
        con_num = [0] * (n1 + n2)
        k = 0
        while i < n1 and j < n2:
            if nums1[i] < nums2[j]:
                con_num[k] = nums1[i]
                i += 1
            else:
                con_num[k] = nums2[j]
                j += 1
            k += 1
        other = nums2[j:] or nums1[i:]
        for num in other:
            con_num[k] = num
            k += 1
        return con_num
```

