数组所有数字都变成一样  需要加减1的总共最小次数
[https://leetcode.com/problems/minimum-moves-to-equal-array-elements-ii/](https://leetcode.com/problems/minimum-moves-to-equal-array-elements-ii/)
```
class Solution {
public:
    int minMoves2(vector<int>& nums) {
        if(nums.size() == 0) return 0;
        sort(nums.begin(), nums.end());
        int ans = 0;
        for(auto x : nums) {//找出中间的那个数为目标数
            ans += abs(x - nums[nums.size() / 2]);
        }
        return ans;
    }
};
```
