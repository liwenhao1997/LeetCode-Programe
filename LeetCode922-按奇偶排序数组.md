## 题目描述

​	给定一个非负整数数组 A， A 中一半整数是奇数，一半整数是偶数。对数组进行排序，以便当 A[i] 为奇数时，i 也是奇数；当 A[i] 为偶数时， i 也是偶数。你可以返回任何满足上述条件的数组作为答案。

## 思路解析

​	由于奇数偶数数量相等，所以只要检查奇数位或偶数位即可。即若奇数位上的数字全为奇数，则偶数位上亦是如此。

## 代码实现

class Solution {

```java
public int[] sortArrayByParityII(int[] A) {
    int j = 1;
    for (int i = 0; i < A.length; i = i + 2) {
        if ((A[i] & 1) != 0) {
            while ((A[j] & 1) != 0) {
                j = j + 2;
            }
            int tmp = A[i];
            A[i] = A[j];
            A[j] = tmp;
        }
    }
    return A;
}
```
}