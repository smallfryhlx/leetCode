求n阶乘的0的个数
Runtime: 4 ms, faster than 59.22% 
Memory Usage: 8.3 MB, less than 78.57%
[https://leetcode.com/problems/factorial-trailing-zeroes/](https://leetcode.com/problems/factorial-trailing-zeroes/)
5进制思想
```
class Solution {
public:
    int trailingZeroes(int n) {
        int res(0);
        while (n) {
            res += n /= 5;
        }
        return res;
    }
};
```
