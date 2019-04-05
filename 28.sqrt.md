* Question

```
Implement int sqrt(int x)

Input: 4
Output: 2

Input: 8
Output: 2
Explanation: The square root of 8 is 2.82842..., and since we want to return an integer, the decimal part will be truncated.

```
使用二分搜索法解决。

```
class Solution(object):
    def mySqrt(self, x):
        try:
            start = 1
            import sys
            end = sys.maxsize
            while 1:
                mid = start + (end - start) / 2
                if mid > x / mid:
                    end = mid - 1
                else:
                    if mid + 1 > x / (mid + 1):
                        return int(mid)
                    start = mid + 1

        except:
            return 0
```

