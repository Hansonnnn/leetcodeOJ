## Problem

Given a string s, find the longest palindromic subsequence's length in s. You may assume that the maximum length of s is 1000.

**Example1**
```
Input:

"bbbab"

Output:
4

One possible longest palindromic subsequence is "bbbb".
```

**Example2**
```
Input:

"cbbd"

Output:
2

One possible longest palindromic subsequence is "bb".

```
## Solution
```python
class Solution(object):
    def longestPalindromeSubseq(self, s):
        """
        :type s: str
        :rtype: int
        """
        if not s: return
        length = len(s)
        res = [[0 for _ in range(length)] for _ in range(length)]
        i = length - 1
        while i >= 0:
            j = i + 1
            res[i][i] = 1
            while j < length:
                if s[i] == s[j]:
                    res[i][j] = res[i + 1][j - 1] + 2
                else:
                    res[i][j] = max(res[i + 1][j], res[i][j - 1])
                j += 1
            i -= 1
        return res[0][len(s) - 1]
```

link:https://leetcode.com/problems/longest-palindromic-subsequence/


