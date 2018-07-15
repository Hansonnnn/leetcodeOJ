Given a string s, find the longest palindromic substring in s. You may assume that the maximum length of s is 1000.

```
Input: "babad"
Output: "bab"
Note: "aba" is also a valid answer.
```

Example 2

```
Input: "cbbd"
Output: "bb"
```
低效做法：
```
class Solution:
    def longestPalindrome(self,s):
        """
        :type s: str
        :rtype: str
        """
        longPalindrome_len = 0
        longPalindrome = ''
        for i in range(len(s)):
            j = 1
            while (j < len(s) + 1):
                s1 = s[i:j]
                if isPalindrome(s1) and (len(s1) > longPalindrome_len):
                    longPalindrome_len = len(s1)
                    longPalindrome = s1
                j += 1

        return longPalindrome


def isPalindrome(s):
    start = 0
    end = len(s) - 1
    while (start < end):
        if (s[start] != s[end]):
            return False
        start += 1
        end -= 1
    return True



