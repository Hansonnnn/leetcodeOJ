## Problem

The string `"PAYPALISHIRING"` is written in a zigzag pattern on a given number of rows like this: (you may want to display this pattern in a fixed font for better legibility)
```
P   A   H   N
A P L S I I G
Y   I   R
```
And then read line by line: `"PAHNAPLSIIGYIR"`

Write the code that will take a string and make this conversion given a number of rows:
```
string convert(string s, int numRows);
```
**Example 1:**
```
Input: s = "PAYPALISHIRING", numRows = 3
Output: "PAHNAPLSIIGYIR"
```
**Example 2:**
```
Input: s = "PAYPALISHIRING", numRows = 4
Output: "PINALSIGYAHRPI"
Explanation:

P     I    N
A   L S  I G
Y A   H R
P     I
```
## Solution

借助 `StringBuilder` 的 `append（）`方法，可以构造三个 `StringBuilder` 数组，用来记录 `z` 字形每一行的字符，对于输入规则，根据观察 `z` 字形排列规则，可以设置一个相当于游标的东西 `pre`，用它来控制输出到哪一个 `StringBuilder` 字符数组当中，`StringBuilder 字符数组的大小就是输入的 `numRows` 大小。最后再将 `numRows个StringBuilder` 数组合并到一块。这道题里面还有一个关键点就是如何控制每行的字符输出，其实关键在处理第一行和最后一行的输出，程序当中可以看到具体的实现方法。

```java
private String converse(String s, int numRows) {
    if(numRows==1){
        return s;
    }
    StringBuilder[] s1=new StringBuilder[numRows];
    for(int i=0;i<s1.length;i++){
        s1[i]=new StringBuilder("");
    }
    int index=0;
    int pre=1;             //类似游标控制输出到的数组
    for(int i=0;i<s.length();i++){
        s1[index].append(s.charAt(i));
        if(index==0){      //处理第一行数据
         pre=1;
        }
        if(index==numRows-1)//处理最后一行数据
        {
            pre=-1;
        }
        index+=pre;
    }
    String res="";
    for(int i=0;i<s1.length;i++)
    {
        res+=s1[i];
    }
    return res;
```

link: https://leetcode.com/problems/zigzag-conversion/

