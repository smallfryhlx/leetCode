翻转数值得2进制数据
[https://leetcode.com/problems/reverse-bits/](https://leetcode.com/problems/reverse-bits/)
Runtime: 4 ms, faster than 68.00%
Memory Usage: 8.1 MB, less than 87.50%
类似于翻转字符串
```
class Solution {
public:
    uint32_t reverseBits(uint32_t n) {
        int times = 16;
        int i = 0;
        uint32_t ret = 0;
        while(i < times)
        {
            ret |= ((n>>(31-i) & 1) <<i) | (((n >> i) & 1)<<(31-i));
            i++;
        }
        return ret;
    }
};
```
