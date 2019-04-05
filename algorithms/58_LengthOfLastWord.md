## Problem

Given a string s consists of upper/lower-case alphabets and empty space characters `' '`, return the length of last word in the string. If the last word does not exist, return 0.

**Note:** 

A word is defined as a character sequence consists of non-space characters only.

**Example:**

```
Input: "Hello World"
Output: 5
```

## Solution
思路：首先去除字符串头和尾的空格，然后根据题目，空格后即为另一个单词的开始，所以使用空格分割，然后获取分割后的最后一个字符即为题目要求，求其长度。

```
class Solution(object):
    def lengthOfLastWord(self, s):
        """
        :type s: str
        :rtype: int
        """
        try:
            s = s.strip()
            chars = s.split(" ")
            return len(chars[len(chars) - 1])
        except:
            return 0
```

link: https://leetcode.com/problems/length-of-last-word/


