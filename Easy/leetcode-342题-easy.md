判断一个数是否为4的n此幂
Runtime: 4 ms, faster than 57.19% of C++ online submissions for Power of Four.
Memory Usage: 8 MB, less than 100.00% of C++ online submissions for Power of Four.
[https://leetcode.com/problems/power-of-four/](https://leetcode.com/problems/power-of-four/)
这个数化成二进制必然是最高位为1 后面2*n个零；
```
class Solution {
public:
    bool isPowerOfFour(int num) {
        if(num == 0)
            return false;
        while (num)
        {
            if(num & 0x11)
            {
                return false;
            }
            num >>= 2;
        }
        return true;
    }
};
```
