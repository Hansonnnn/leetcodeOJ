* Question
```
Given two binary strings, return their sum (also a binary string).

For example,
a = "11"
b = "1"
Return "100".

```
* solution 1: 利用python的内置函数bin

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

