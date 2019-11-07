将后面k个数移到数组前面，经过三个逆转操作比较方便，但是速度不理想
Runtime: 20 ms, faster than 30.94%
Memory Usage: 9.5 MB, less than 88.89%
[https://leetcode.com/problems/rotate-array/](https://leetcode.com/problems/rotate-array/)
####实现代码
```
class Solution {
public:
    void rotate(vector<int>& nums, int k) {
        int len = nums.size();
        k %= len;
        reverse(nums,0,len-1);
        reverse(nums,0,k-1);
        reverse(nums,k,len-1);
    }

private:
    void reverse(vector<int> &v,int begin,int end)
    {
        while(begin < end)
        {
            std::swap(v[begin],v[end]);
            begin ++;
            end --;
        }
    }
};
```
