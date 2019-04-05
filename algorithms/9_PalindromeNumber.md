## Problem
Determine whether an integer is a palindrome. An integer is a palindrome when it reads the same backward as forward.

**Example 1:**
```
Input: 121
Output: true
```
**Example 2:**
```
Input: -121
Output: false
Explanation: From left to right, it reads -121. From right to left, it becomes 121-. Therefore it is not a palindrome.
```
**Example 3:**
```
Input: 10
Output: false
Explanation: Reads 01 from right to left. Therefore it is not a palindrome.
```

## Solution
```java
class Solution {
    public boolean isPalindrome(int x) {
        if(x<0){
            return false;
        }
        int y=x;
        int result=0;
        while(x!=0){
            int tail=x%10;
            int newResult=result*10+tail;
            if((newResult-tail)/10!=result){
                return false;
            }
            result=newResult;
            x=x/10;
        }
        if(result==y){
            return true;
        }else{
            return false;
        }
    }
}
```

link: https://leetcode.com/problems/palindrome-number/
:1

