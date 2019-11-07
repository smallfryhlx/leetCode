求int sqrt(int num);
二分法
Runtime: 4 ms, faster than 75.04%
Memory Usage: 8.2 MB, less than 100.00%
####实现代码
```
class Solution {
public:
    int mySqrt(int x) {
        int begin = 1;
        int end = x;
        int middle = (end-begin)/2+begin;
        while (begin <= end)
        {
            if(middle <= x/middle && (middle+1) > x/(middle+1))
            {
                return middle;
            } else if(middle > x/middle){
                end = middle - 1;
            }else{
                begin = middle + 1;
            }
            middle = (end-begin)/2+begin;
        }
    }
};
```
