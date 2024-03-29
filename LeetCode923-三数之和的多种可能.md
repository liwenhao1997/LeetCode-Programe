## 题目描述

​	给定一个整数数组 A，以及一个整数 target 作为目标值，返回满足 i < j < k 且 A[i] + A[j] + A[k] == target 的元组 i, j, k 的数量。

## 思路解析

​	使用桶排序，针对给定的大小初始化桶，桶中数字即为该桶下标对应的数字在源数组中出现的次数。

## 代码实现

```java
public static int threeSumMulti(int[] A, int target) {
        long result = 0;
        long[] numbers = new long[101]; // 0 <= A[i] <= 100
        for (int i: A) {
            numbers[i]++;
        }
        int min = 0;
        while (numbers[min] == 0) {
            min++;
        }
        int max = 100;
        while (numbers[max] == 0) {
            max--;
        }
        int i = min;
        while (i <= max) {
            int j = i;
            while (j <= max) {
                int key = target - i - j;
                if (key >= i && key <= j && numbers[key] > 0) {
                    if (i == key && i != j) {
                        result += numbers[j] * ((numbers[i] - 1) * numbers[i] / 2);
                    }else if (j == key && i != j) {
                        result += numbers[i] * ((numbers[j] - 1) * numbers[j] / 2);
                    }else if (i == j && j == key) {
                        result += numbers[i] * (numbers[i] - 1) * (numbers[i] - 2) / 6;
                    }else{
                        result += numbers[i] * numbers[j] * numbers[key];
                    }
                }
                do {
                    j++;
                } while (j < max && numbers[j] == 0);
            }
            do {
                i++;
            } while (i < max && numbers[i] == 0);
        }
        return (int)(result % 1000000007);
    }
```
