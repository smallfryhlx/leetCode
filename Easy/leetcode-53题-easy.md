求数组中所有子数组中和最大的那个值
Runtime: 8 ms, faster than 71.67% 
Memory Usage: 9.1 MB, less than 100.00% 
[https://leetcode.com/problems/maximum-subarray/](https://leetcode.com/problems/maximum-subarray/)
```
class Solution {
public:
    int maxSubArray(vector<int>& nums) {
        int len = nums.size();
        if(len == 0)
            return 0;
        int sum = nums[0];
        int max = sum;
        for(int i = 1; i < len; i++)
        {
            int tmp = sum + nums[i];
            if(tmp > nums[i])
            {
                sum = tmp;
            }else{
                sum = nums[i];
            }
            if(max < sum)
                max = sum;
        }
        return max;
    }
};
```
