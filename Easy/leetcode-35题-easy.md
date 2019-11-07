吧一个数字插入到数组应该插到哪个位置？
[https://leetcode.com/problems/search-insert-position/](https://leetcode.com/problems/search-insert-position/)
Runtime: 4 ms, faster than 98.54% of C++ online submissions for Search Insert Position.
Memory Usage: 8.8 MB, less than 93.75% of C++ online submissions for Search Insert Position.
O(n)时间复杂度
```
class Solution {
public:
    int searchInsert(vector<int>& nums, int target) {
        int len = nums.size();
        int i = 0;
        if(nums[0] >= target)
            return 0;
        if(nums[len-1] <= target)
        {
            return nums[len-1] == target ? len - 1 : len;
        }

        int j = len-1;
        int mid = (j-i)/2+i;
        while(i <= j)
        {
            if(nums[mid] >= target && target>=nums[mid-1])
            {
                cout<<"ret"<<endl;
                return target ==nums[mid-1]?mid -1 : mid;
            }else if(target > nums[mid]){
                j = mid - 1;
            }else{
                i = mid + 1;
            }
            mid = (j-i)/2+i;
        }
        return -1;
    }
};
```
