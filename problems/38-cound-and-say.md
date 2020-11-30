# 38. Count and Say
 [Count and Say](https://leetcode.com/problems/count-and-say/)

这一题的难点在于理解题意。

按照下面的递归形式定义数字字符串：

- `countAndSay(1) = "1"`
- `countAndSay(n)`是你怎么说`countAndSay(n -1)`。

说`countAndSay(n -1)`的方式如下：

如果有字符串`"3322251"`，那么说这个字符串的数字字符串这样构造：

![countandsay](../asserts/38-cound-and-say/countandsay.jpg)

```c++
class Solution {
   public:
    string countAndSay(int n) {
        if (n <= 0) {
            return "";
        }
        std::string ret = "1";
        while (--n != 0) {
            std::string current_str;
            for (std::size_t i = 0; i < ret.size(); ++i) {
                std::size_t cnt = 1;
                while (i + 1 < ret.size() && ret[i] == ret[i + 1]) {
                    ++cnt;
                    ++i;
                }
                current_str += (std::to_string(cnt) + ret[i]);
            }
            ret = current_str;
        }
        return ret;
    }
};
```

