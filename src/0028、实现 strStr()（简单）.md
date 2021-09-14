## 问题描述
> 这是 LeetCode 上的 [28. 实现 strStr()](https://leetcode-cn.com/problems/implement-strstr/)，难度为 **简单**。
> 
> 关键字： `字符串`、`KMP（我暂时还不会）`

实现 `strStr()` 函数。

给你两个字符串 `haystack` 和 `needle` ，请你在 `haystack` 字符串中找出 `needle` 字符串出现的第一个位置（下标从 `0` 开始）。如果不存在，则返回  `-1` 。

**说明：**

当 `needle` 是空字符串时，我们应当返回什么值呢？这是一个在面试中很好的问题。

对于本题而言，当 `needle` 是空字符串时我们应当返回 `0` 。这与 `C` 语言的 `strstr()` 以及 `Java` 的 `indexOf()` 定义相符。

**示例 1：**
```
输入：haystack = "hello", needle = "ll"
输出：2
```

**示例 2：**
```
输入：haystack = "aaaaa", needle = "bba"
输出：-1
```

**示例 3：**
```
输入：haystack = "", needle = ""
输出：0
```

**提示：**
1. `0 <= haystack.length, needle.length <= 5 * 104`
2. `haystack` 和 `needle` 仅由小写英文字符组成

<hr>

## 暴力解法
遍历 `原串` 中每个字符作为 `初始字符`，然后 从原串的初始字符开始与目标字符串的每个字符进行匹配。
1. 完全一致匹配：返回当前的字符。
2. 匹配失败：原串的下一个字符作为 `初始字符`，重新进行匹配。
```java
class Solution {
    public int strStr(String haystack, String needle) {
        if (needle.isEmpty()) {
            return 0;
        }
        int h = haystack.length(), n = needle.length();
        char[] hs = haystack.toCharArray(), ns = needle.toCharArray();
        // 从 0 遍历到 原串与目标串的差值，即去掉目标串剩下的字符串长度
        for (int i = 0; i <= h - n; i++) {
            int a = i, b = 0;
            // 一个字符一个字符判断
            while(b < n && hs[a] == ns[b]) {
                ++a;
                ++b;
            }
            // 如果完全一致，返回当前
            if (b == n) {
                return i;
            }
        }
        // 其他返回失败
        return -1;
    }
}
```

## KMP算法
暂时不太会，以后补充！！！

<hr>

## 引用
我的 `github` 仓库已经同步建立，[https://github.com/haonange1314/defeat-leetcode](https://github.com/haonange1314/defeat-leetcode)
