//合并两个有序数组为一个 逆向赋值
Runtime: 4 ms, faster than 84.26% 
Memory Usage: 8.8 MB, less than 65.22%
[https://leetcode.com/problems/merge-sorted-array/](https://leetcode.com/problems/merge-sorted-array/)
```
class Solution {
public:
    void merge(vector<int>& nums1, int m, vector<int>& nums2, int n) {
        int len = m+n;
        int i = m-1;
        int j = n-1;
        int k = m+n-1;
        while(i>=0 && j>=0)
        {
            if(nums1[i] > nums2[j])
            {
                nums1[k--] = nums1[i--];
            }else{
                nums1[k--] = nums2[j--];
            }
        }
        while(i>=0)
        {
            nums1[k--] = nums1[i--];
        }
        while(j>=0)
        {
            nums1[k--] = nums2[j--];
        }
    }
};
```
