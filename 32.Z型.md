#### 字符串输入按z字形并输入z字形行数，排列再输出另一字符串

example：
input：PAYPALISHIRING   3

between：P   A   H   N
         A P L S I I G
         Y   I   R

output：PAHNAPLSIIGYIR

>思路：思路是这样的，借助StringBuilder的append（）方法，可以构造三个StringBuilder数组，用来记录z字形每一行的字符，对于输入规则，根据观察z字形排列规则，可以设置一个相当于游标的东西pre，用它来控制输出到哪一个StringBuilder字符数组当中，StringBuilder字符数组的大小就是输入的numRows大小。最后再将numRows个StringBuilder数组合并到一块。这道题里面还有一个关键点就是如何控制每行的字符输出，其实关键在处理第一行和最后一行的输出，程序当中可以看到具体的实现方法。

```
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
