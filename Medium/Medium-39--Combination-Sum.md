递归 比较暴力 所以效果也不好
[https://leetcode.com/problems/combination-sum/](https://leetcode.com/problems/combination-sum/)

```
class Solution {
public:
    vector<vector<int>> combinationSum(vector<int>& candidates, int target) {
        vector<vector<int>> ans;
        vector<int> nums;
        help(candidates,target,ans,nums,candidates.size()-1);

        return ans;
    }

private:
    void help(vector<int>& candidates, int target,vector<vector<int>> &ans, vector<int> nums,int index)
    {
        if(index < 0 || target < 0)
            return;
        help(candidates,target,ans,nums,index-1);
        int i = 1;
        while( candidates[index] <= target)
        {
            nums.emplace_back(candidates[index]);
            target = target - candidates[index] ;
            if(target == 0)
            {
                ans.emplace_back(nums);
                return;
            }else if(target < 0)
                return;
            help(candidates,target,ans,nums,index-1);
            i++;
        }
    }
};
```
