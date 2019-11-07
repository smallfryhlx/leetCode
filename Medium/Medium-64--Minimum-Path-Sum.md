[https://leetcode.com/problems/minimum-path-sum/](https://leetcode.com/problems/minimum-path-sum/)
MxN的数组 只能向右 向下走 怎么走可以使消耗最小
典型的dp算法
```
class Solution {
public:
    int minPathSum(vector<vector<int>>& grid) {
        vector<vector<int>> dp(grid.size(),vector<int>(grid[0].size(),0));
        dp[0][0] = grid[0][0];
        int sum1 = dp[0][0];
        for(int i = 1;i <grid.size();i++)
        {
            sum1 += grid[i][0];
            dp[i][0]= sum1;
        }
        int sum2 = dp[0][0];
        for(int j = 1; j < grid[0].size();j++)
        {
            sum2 += grid[0][j];
            dp[0][j] = sum2;
        }

        for(int i = 1;i < grid.size();i++)
            for(int j = 1; j <grid[0].size();j++)
            {
                dp[i][j] = min(dp[i-1][j],dp[i][j-1]) + grid[i][j];
            }
        return dp[dp.size()-1][dp[0].size()-1];
    }
};
```
