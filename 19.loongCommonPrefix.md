##### Problem
Write a function to find the longest common prefix string amongst an array of strings.

If there is no common prefix, return an empty string "".

###### Example1:
```
Input: ["flower","flow","flight"]
Output: "fl"
```

###### Example2:
```
Input: ["dog","racecar","car"]
Output: ""
Explanation: There is no common prefix among the input strings.
```
###### Note:

All given inputs are in lowercase letters a-z.

##### Solution
```
class Solution:
    def longestCommonPrefix(self, strs) -> str:
        if len(strs) == 0 or strs is None:
            return ''
        return self._longestCommonPrefix(strs, 0, len(strs) - 1)

        pass

    def _longestCommonPrefix(self, strs, left, right):
        if left == right:
            return strs[left]
        else:
            mid: int = int((left + right) / 2)
            prefix_left = self._longestCommonPrefix(strs, left, mid)
            prefix_right = self._longestCommonPrefix(strs, mid + 1, right)

            return self._common_prefix(prefix_left, prefix_right)

    def _common_prefix(self, prefix_left, prefix_right):
        min_len: int = min(len(prefix_left), len(prefix_right))
        for i in range(min_len):
            if prefix_left[i] != prefix_right[i]:
                return prefix_left[:i]
        return prefix_left[:min_len]
