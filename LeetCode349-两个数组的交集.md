## 题目描述

	给定两个数组，编写一个函数来计算它们的交集。

示例 1:

​	输入: nums1 = [1,2,2,1], nums2 = [2,2]
​	输出: [2]

示例 2:

​	输入: nums1 = [4,9,5], nums2 = [9,4,9,8,4]
​	输出: [9,4]

## 代码实现

```java
public static int threeSumMulti(int[] A, int target) {
        int max = Integer.MIN_VALUE;
        int min = Integer.MAX_VALUE;
        for (int num : nums1) {
            if (num > max) {
                max = num;
            }
            if (num < min) {
                min = num;
            }
        }
        int range = max - min + 1;
        boolean[] arr = new boolean[range];
        for (int num : nums1) {
            arr[num - min] = true;
        }
        int[] temp = new int[range];
        int idx = 0;
        for (int num : nums2) {
            if (num >= min && num <= max && arr[num - min]) {
                temp[idx++] = num;
                arr[num - min] = false;
            }
        }
        int[] result = new int[idx];
        for (int i = 0; i < idx; i++) {
            result[i] = temp[i];
        }
        return result;
    }
```
