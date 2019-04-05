#### lengthOfLongestSubstring

问题描述

Given a string, find the length of the longest substring without repeating characters.

Examples:

* Given "abcabcbb", the answer is "abc", which the length is 3.

* Given "bbbbb", the answer is "b", with the length of 1.

* Given "pwwkew", the answer is "wke", with the length of 3. Note that the answer must be a substring, "pwke" is a subsequence and not a substring.


>思路：这一题放在中等难度中，题目本省不难，就是求出某个字符串中的最长得不重复子串的长度。那么可以从字符串得第一个元素开始逐个迭代，并设立一个临时空间用来存放不重复子串，然后再从第二个开始迭代，直至所有元素迭代完成。在迭代过程中需要不断更新最大子串长度

代码：

```
    def lengthOfLongestSubstring(self, s):
        if len(s) == 0:
            return 0
        tmp = {}
        start = 0
        max_len = 0
        for i in range(len(s)):
            if s[i] in tmp:
                max_len = max(max_len, i-start)
                start = max(start,tmp[s[i]]+1)
            tmp[s[i]] = i
        return max(max_len,len(s)-start)
```

