### Question
```
Given two binary strings, return their sum (also a binary string).

For example,
a = "11"
b = "1"
Return "100".

```
### Solution 

1: 利用 python 的内置函数 bin

```
class Solution(object):
    def addBinary(self, a, b):
        """
        :type a: str
        :type b: str
        :rtype: str
        """
        result = bin(int(a, 2) + int(b, 2))[2:]
        return result
```

link: https://leetcode.com/problems/add-binary/

