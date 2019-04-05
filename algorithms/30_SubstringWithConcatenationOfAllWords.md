## Problem

You are given a string, **s**, and a list of words, **words**, that are all of the same length. Find all starting indices of substring(s) in s that is a concatenation of each word in **words** exactly once and without any intervening characters.

**Example 1:**
```
Input:
  s = "barfoothefoobarman",
  words = ["foo","bar"]
Output: [0,9]
Explanation: Substrings starting at index 0 and 9 are "barfoor" and "foobar" respectively.
The output order does not matter, returning [9,0] is fine too.
```
**Example 2:**
```
Input:
  s = "wordgoodgoodgoodbestword",
  words = ["word","good","best","word"]
Output: []
```

## Solution

设立两个hash，一个是一开始存入所有的单词表，还有一个是进行判断有多少个相同长度的单词。
主要是进行滑块类似的判断。

```java
class Solution {
    public List<Integer> findSubstring(String s, String[] words) {
        
        List<Integer> res=new ArrayList<>();
        if(s==null||s==""||words==null||words.length==0){
            return res;
        }
        int len=words[0].length();
        Map<String,Integer>map=new HashMap<String,Integer>();
        for(String tmp:words){
            if(!map.containsKey(tmp)){
                map.put(tmp,1);
            }
        }
        for(int i=0;i<s.length()-words.length*len;i++){
            Map<String,Integer>map1=new HashMap<String,Integer>();//滑块
            for(int j=0;j<words.length;j++)
            {
                String tmp_Stringstring=s.substring(i+j*len,i+j*len+len);
                if(!map1.containsKey(tmp_Stringstring)){
                    map1.remove(tmp_Stringstring);
                }else{
                    continue;
                }
            }
            if(map1.isEmpty()){
                res.add(i);
            }
        }
        return res;
        
    }
}
```
代码待优化。

link: https://leetcode.com/problems/substring-with-concatenation-of-all-words/

