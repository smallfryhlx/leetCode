1-n个版本，找出哪个版本最开始有问题的，二分法
Runtime: 4 ms, faster than 50.50%
Memory Usage: 8.2 MB, less than 75.76%
[https://leetcode.com/problems/first-bad-version/](https://leetcode.com/problems/first-bad-version/)
####代码实现
```
class Solution {
public:
    int firstBadVersion(int n) {
        int begin = 1;
        int end = n;
        int middle = (end - begin)/2 + begin;
        while(begin <= end)
        {
            bool isBadMiddle = isBadVersion(middle);
            if(isBadMiddle && !isBadVersion(middle-1))
            {
                return middle;
            }else if(isBadMiddle){
                end = middle;
            }else{
                begin = middle+1;
            }
            middle = (end - begin)/2 + begin;
        }
        return 0;
    }
};
```
