Runtime: 28 ms, faster than 57.15% of C++ online submissions for Find Pivot Index.
Memory Usage: 9.9 MB, less than 71.43% of C++ online submissions for Find Pivot Index.
[https://leetcode.com/problems/find-pivot-index/](https://leetcode.com/problems/find-pivot-index/)
求第一个分界点使得左右两边的和相等
···
class Solution {
public:
    int pivotIndex(vector<int>& nums) {
        int right = 0;
        int len = nums.size();
        if(len <= 2)
            return -1;
        for(int i = 1; i < len ; i++)
        {
            right += nums[i];
        }
        int j = 0;
        int left = 0;
        while(j < len)
        {
            if(left == right)
            {
                return j;
            }else{
                if(j == len - 1)
                {
                    if(left == 0)
                        return j;
                    return -1;
                }else{
                    left += nums[j];
                    right -= nums[j+1];
                    j++;
                }
            }
        }
        return -1;
    }
};
···
