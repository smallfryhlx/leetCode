[https://leetcode.com/problems/remove-duplicates-from-sorted-array/](https://leetcode.com/problems/remove-duplicates-from-sorted-array/)
Runtime: 24 ms, faster than 59.97%
Memory Usage: 10 MB, less than 73.75%
···
class Solution {
public:
    int removeDuplicates(vector<int>& nums) {
       int len = nums.size();
        if(len == 0)
            return 0;
        int i = 0;
        int j = 1;
        while(j < len)
        {
            if(nums[j] == nums[i])
            {
                j++;
            }else{
                i++;
                nums[i] = nums[j];
                j++;
            }
        }
        //print(nums);
        return  i+1; 
    }
};
···
