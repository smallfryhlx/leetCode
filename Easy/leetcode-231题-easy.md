求一个数是不是2的n次方
Runtime: 4 ms, faster than 55.81% 
Memory Usage: 7.9 MB, less than 100.00%
```
class Solution {
public:
    bool isPowerOfTwo(int n) {
        int count = 0;
        if(n == 0)
            return false;
        while(n)
        {
            if(n &0x01)
                count++;
            if(count >= 2)
                return false;
            n >>= 1;
        }
        return true;
    }
};
```
