将一个数组的子数组排序后使得数组为有序数组，求这个子数组的最小长度
Runtime: 36 ms, faster than 74.77% 
Memory Usage: 10.4 MB, less than 95.24%
[https://leetcode.com/problems/shortest-unsorted-continuous-subarray/](https://leetcode.com/problems/shortest-unsorted-continuous-subarray/)
思路：找出子数组的开头跟结尾即可
####代码实现
```
class Solution {
public:
    int findUnsortedSubarray(vector<int>& nums) {
        int len = nums.size();
        if(len <= 1)
            return 0;
        int i = 0;
        int j = len -1;
        int first_desc_index = -1;
        int first_increase_index = -1;
        int begin = 0;
        int end = len-1;
        while(i < len - 1)
        {
            if(nums[i] > nums[i+1])
            {
                first_desc_index = i+1;
                break;
            }
            i++;
        }
        if(first_desc_index != -1)
        {
            int find_after_arr_min = nums[first_desc_index];
            for(int index = first_desc_index;index < len;index++)
                if(find_after_arr_min > nums[index])
                    find_after_arr_min = nums[index];

            for(int index = 0;index < first_desc_index;index++)
                if(nums[index] > find_after_arr_min)
                {
                    begin = index;
                    break;
                }
        }else{
            return 0;
        }
        while(j >= 1)
        {
            if(nums[j] < nums[j-1])
            {
                first_increase_index = j-1;
                break;
            }
            j--;
        }
        if(j == 0)
        {
            return 0;
        }else{
            int find_before_arr_max = nums[first_increase_index];
            for(int index = 0;index < first_increase_index ;index++)
                if(nums[index] > find_before_arr_max)
                    find_before_arr_max = nums[index];
            for(int index = first_increase_index+1;index < len;index++)
                if(nums[index] >= find_before_arr_max)
                {
                    end = index - 1;
                    break;
                }
        }
        return end - begin + 1;
    }
};
```
