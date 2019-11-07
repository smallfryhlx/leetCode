求一个数是否为平方数
Runtime: 0 ms, faster than 100.00%
Memory Usage: 8 MB, less than 100.00% 
[https://leetcode.com/problems/valid-perfect-square/](https://leetcode.com/problems/valid-perfect-square/)
二分法
```
class Solution {
public:
    bool isPerfectSquare(int num) {
        int i = 1;
        int j = num;
        int mid = (j-i)/2+i;
        while(i <= j)
        {
            auto k = num/mid;
            auto k2 = num/(mid+1)-1;
            if(mid <= k && mid > k2)
            {
                break;
            }else if(mid > k){
                j = mid -1;
            }else{
                i = mid + 1;
            }
            mid = (j-i)/2+i;
        }
        return mid*mid == num;
    }
};
```
