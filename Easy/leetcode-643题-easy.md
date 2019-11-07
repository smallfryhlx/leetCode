求数组的长度为k的子数组和最大的那个值，
Runtime: 172 ms, faster than 77.56%
Memory Usage: 16.9 MB, less than 33.33%
[https://leetcode.com/problems/maximum-average-subarray-i/](https://leetcode.com/problems/maximum-average-subarray-i/)

不要重复计算
```
class Solution {
public:
    double findMaxAverage(vector<int>& nums, int k) {
        auto len = nums.size();
        double ret = 0;
        double sumk = 0;
        for(int j = 0;j<k;j++)
        {
            sumk+= nums[j];
        }
        ret = sumk;
        //cout<<len<<endl;
        for(int i = 1;i < (len - k + 1);i++)
        {
            sumk = sumk + nums[i+k-1] - nums[i-1];
            if(ret < sumk)
                ret = sumk;
        }
        return ret/k;
    }
};
```
