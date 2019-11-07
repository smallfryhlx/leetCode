[https://leetcode.com/problems/sum-of-square-numbers/](https://leetcode.com/problems/sum-of-square-numbers/)
Runtime: 0 ms, faster than 100.00%
Memory Usage: 8.1 MB, less than 83.33%
```
class Solution {
public:
    bool judgeSquareSum(int c) {
        //a litter b bigger;
        int i = 0;
        auto end = static_cast<int>(std::sqrt(c / 2));
        for(;i<=end;i++)
        {
            if(isSquare(c-i*i)){
                return true;
            }
        }
        return false;
    }
private:
    bool isSquare(int a)
    {
        auto b = static_cast<int>(std::sqrt(a));
        return b*b==a;
    }
};
```
