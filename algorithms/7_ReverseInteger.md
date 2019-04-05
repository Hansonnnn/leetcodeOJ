## Problem
Given a 32-bit signed integer, reverse digits of an integer.

**Example 1:**
```
Input: 123
Output: 321
```
**Example 2:**
```
Input: -123
Output: -321
```
**Example 3:**
```
Input: 120
Output: 21
```

## Solution
解法有两个关键点，第一while循环，有了while循环就可以不管数有多大（2147483648~2147483647：java中的整型变量取值范围，java中int占4个字节）取值最后一位，第二就是关于while循环中的溢出判断，通过这层判断就可以>避免溢出。还有就是也对负数完美解决。

```java
public int reverse(int x){
    int result = 0;
    while (x != 0)
    {
        int tail = x % 10;
        int newResult = result * 10 + tail;
        if ((newResult - tail) / 10 != result)
        { return 0; }
        result = newResult;
        x = x / 10;
    }
    return result;
}
```
运行结果：
```
Runtime: 1 ms, faster than 100.00% of Java online submissions for Reverse Integer.
Memory Usage: 32.4 MB, less than 100.00% of Java online submissions for Reverse Integer.
```

link: https://leetcode.com/problems/reverse-integer/


