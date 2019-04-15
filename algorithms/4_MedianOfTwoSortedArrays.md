## Problem
There are two sorted arrays **nums1** and **nums2** of size m and n respectively.

Find the median of the two sorted arrays. The overall run time complexity should be O(log (m+n)).

You may assume **nums1** and **nums2** cannot be both empty.

**Example 1:**
```
nums1 = [1, 3]
nums2 = [2]

The median is 2.0
```
**Example 2:**
```
nums1 = [1, 2]
nums2 = [3, 4]

The median is (2 + 3)/2 = 2.5
```
## Solution
```
class Solution:
    def findMedianSortedArrays(self, nums1, nums2) -> float:
        INT_MAX = 2147483647
        INT_MIN = (-INT_MAX - 1)
        N1: int = len(nums1)
        N2: int = len(nums2)
        if N2 > N1:
            return self.findMedianSortedArrays(nums2, nums1)
        lo = 0
        hi = N2 * 2
        while lo <= hi:
            mid2 = (lo + hi) // 2
            mid1 = N1 + N2 - mid2

            l1: float = INT_MIN if (mid1 == 0) else nums1[(mid1 - 1) // 2]
            l2: float = INT_MIN if (mid2 == 0) else nums2[(mid2 - 1) // 2]
            r1: float = INT_MAX if (mid1 == N1 * 2) else nums1[mid1 // 2]
            r2: float = INT_MAX if (mid2 == N2 * 2) else nums2[mid2 // 2]

            if l1 > r2:
                lo = mid2 + 1
            elif l2 > r1:
                hi = mid2 - 1
            else:
                return (max(l1, l2) + min(r1, r2)) / 2
        return -1
```

link: https://leetcode.com/problems/median-of-two-sorted-arrays/

