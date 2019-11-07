求数组i-j的差值
Runtime: 28 ms, faster than 92.73% 
Memory Usage: 17.3 MB, less than 72.41% 
[https://leetcode.com/problems/range-sum-query-immutable/](https://leetcode.com/problems/range-sum-query-immutable/)

先计算好前k个的差值 然后直接相见即可
```
class NumArray {
public:
    explicit NumArray(vector<int>& nums) {
        int j_sum = 0;
        int len = nums.size();
        for(int j = 0;j<len;j++)
        {
            j_sum += nums[j];
            v.emplace_back(j_sum);
        }
    }
    int sumRange(int i, int j) {
        if(i==0)
            return v[j];
        return v[j] - v[i-1];
    }
private:
    vector<int> v;
};
```
