### Implement strStr()

>Implement strStr().

>Returns the index of the first occurrence of needle in haystack, or -1 if needle is not part of haystack.

>思路:这题不难,但是我第一次使用python A的第一道题,题目意思很明显，如果给定一段字符串包含在另外一个大字符串中就返回在大字符串中第一次出现时的索引，这里我采用了“滑块”的解决思路，以小字符串的长度为滑块大小，在大字符串中循环移动，当所循环到的字符串与滑块中的字符串内容相等时，即返回字符串第一个元素在大字符串中的索引位置。

```
class Solution(object):
    def strStr(self, haystack, needle):
        k =0
        len1 = len(haystack)
        len2 = len(needle)
        if ((len1 == 0 and len2 == 0) or len2 == 0 ):
            return 0
        elif len2> len1:
            return -1
        while k < len1:
            if haystack[k:k+len2] == needle:
                return k
            k=k+1
        return -1
        
```
