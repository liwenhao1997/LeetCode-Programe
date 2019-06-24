## 题目描述

	给定两个数组，编写一个函数来计算它们的交集。

示例 1:

​	输入: nums1 = [1,2,2,1], nums2 = [2,2]
​	输出: [2,2]

示例 2:

​	输入: nums1 = [4,9,5], nums2 = [9,4,9,8,4]
​	输出: [9,4]

## 思路解析

先排序，然后使用下标同步比较各值。

## 代码实现

```java
public static int threeSumMulti(int[] A, int target) {
        Arrays.sort(nums1);
        Arrays.sort(nums2);
        int i = 0, j = 0;
        int[] ans = new int[nums2.length];
        int index = 0;
        while (i++ < nums1.length && j++ < nums2.length) {
            if (nums1[i - 1] == nums2[j - 1]) {
                ans[index++] = nums1[i - 1];
            } else if (nums1[i - 1] < nums2[j - 1]) {
                j--;
            }else {
                i--;
            }
        }
        return Arrays.copyOf(ans, index);
    }
```
