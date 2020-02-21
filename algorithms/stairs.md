## Problem

有n级楼梯，有2种爬法，1次1级，或1次2级，问，n级楼梯有多少种爬法？

##### Example:

```
n =7

1+2+1+1+2=7
1+1+1+1+1+1+1=7

```

##### Solution:

递归解法：

```java
    public static int recurse(int n) {
        if (n == 0 || n == 1 || n == 2) {
            return n;
        } else {
            return recurse(n - 1) + recurse(n + 2);
        }
    }
```

非递归解法（推荐，效率高）：

```java
    public static int stairs(int n) {
        if (n == 0 || n == 1 || n == 2) {
            return n;
        } else {
            int s1 = 1;
            int s2 = 2;
            int temp = 0;
            for (int i = 3; i < n + 1; i++) {
                temp = s1 + s2;
                s1 = s2;
                s2 = temp;
            }
            return temp;
        }
    }
```



