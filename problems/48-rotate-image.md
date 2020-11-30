# 48. Rotate Image

[Rotate Image](https://leetcode.com/problems/rotate-image/)

## 次对角线

沿次对角线元素互换，将每一行倒序。

```c++
class Solution {
   public:
    void rotate(vector<vector<int>>& matrix) {
        const std::size_t n = matrix.size();
        for (std::size_t i = 0; i < n - 1; ++i) {
            for (std::size_t j = 0; j < n - i; ++j) {
                std::swap(matrix[j][i], matrix[n - 1 - i][n - 1 - j]);
            }
        }
        std::reverse(matrix.begin(), matrix.end());
    }
};
```

## 主对角线

沿主对角线元素交换，将每一列元素倒序。

```c++
class Solution {
   public:
    void rotate(vector<vector<int>>& matrix) {
        const std::size_t n = matrix.size();
        for (std::size_t j = 0; j < n; ++j)  // row
        {
            for (std::size_t i = j; i < n; ++i)  // col
            {
                std::swap(matrix[j][i], matrix[i][j]);
            }
            std::reverse(matrix[j].begin(), matrix[j].end());
        }
    }
};
```

## 参考

[https://www.cnblogs.com/grandyang/p/4389572.html](https://www.cnblogs.com/grandyang/p/4389572.html)