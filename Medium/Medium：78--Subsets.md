求数组的所有子数组 
```
class Solution {
public:
    vector<vector<int>> subsets(vector<int>& nums) {
        vector<vector<int>> ans;
        vector<int> cur;
        ans.emplace_back(cur);
        help(nums,0,ans,cur,true);
        help(nums,0,ans,cur,false);
        return ans;
    }

private:
    //index 第index个数据
   //cur 当前子数组 
    //include 加或者不加
    void help(vector<int>& nums,int index, vector<vector<int>>& ans,vector<int>cur,bool include)
    {
        if(index >= nums.size())
            return;
        if(include)
        {
            cur.emplace_back(nums[index]);
            ans.emplace_back(cur);
        }
        help(nums,index+1,ans,cur,true);
        help(nums,index+1,ans,cur,false);
    }
};
```
