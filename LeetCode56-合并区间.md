## 题目描述

​	给出一个区间的集合，请合并所有重叠的区间。

## 思路解析

​	判断两个数组，前一个数组的左边界是否在后一个的区间内，或后一个数组的左边界是否在前一个的区间内。

## 代码实现

```java
public int[][] merge(int[][] a) {
        int n = a.length;
        int count = 0;
        if (n == 0)
            return new int[0][];
        for (int i = 0; i < n-1; i++) {
            int left1 = a[i][0];
            int right1 = a[i][1];
            for (int j = i + 1; j < n ; j++) {
                int left2 = a[j][0];
                int right2 = a[j][1];
                if ((left1 >= left2 && left1 <= right2) || (left2 >= left1 && left2 <= right1)) {
                    count++;
                    a[j][0] = Math.min(a[i][0], a[j][0]);
                    a[j][1] = Math.max(a[i][1], a[j][1]);
                    a[i] = null;
                    break;
                }
            }
        }
        int[][] res = new int[n - count][2];
        int m = 0;
        for (int i = 0; i < a.length; i++) {
            if (a[i] != null)
                res[m++] = a[i];
        }
        return res;
    }
```



