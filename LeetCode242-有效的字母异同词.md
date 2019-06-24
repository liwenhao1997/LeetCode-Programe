## 题目描述

​	给定两个字符串 *s* 和 *t* ，编写一个函数来判断 *t* 是否是 *s* 的字母异位词。

## 思路解析

​	利用桶算法，将字符分布在不同的桶中，每出现一次就将相对位置上的数字加1，同时目标串出现则减一，最后检查数组元素是否均为0。

## 代码实现

```java
public boolean isAnagram(String s, String t) {
        if (s.length() != t.length()) {
            return false;
        }
        int[] arr = new int[26];
        for (int i = 0; i < s.length(); i++) {
            arr[s.charAt(i) - 'a']++;
            arr[t.charAt(i) - 'a']--;
        }

        for (int i : arr) {
            if (i != 0) {
                return false;
            }
        }
        return true;
    }
```



