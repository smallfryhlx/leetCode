唯一路径  dp算法
[https://leetcode.com/problems/unique-paths/](https://leetcode.com/problems/unique-paths/)
```
class Solution {
public:
    int uniquePaths(int m, int n) {
        vector<vector<int>> dp(m,vector<int>(n,0));
        for(int i = 0; i < m;i++)
            dp[i][0] = 1;
        for(int j = 0;j<n;j++)
            dp[0][j] = 1;

        for(int i = 1 ; i < m;i++ )
            for(int j = 1; j < n;j++)
                dp[i][j] = dp[i-1][j] + dp[i][j-1];
        cout<<dp[m-1][n-1]<<endl;
        return dp[m-1][n-1];
    }
};
```
