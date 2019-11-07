两个数组相同字符连线  线不交叉的最多线条数
dp算法
[https://leetcode.com/problems/uncrossed-lines/](https://leetcode.com/problems/uncrossed-lines/)
```
class Solution {
public:
    int maxUncrossedLines(vector<int>& A, vector<int>& B) {
        vector<vector<int>> dp(A.size()+1,vector<int >(B.size()+1,0));
        for(int i = 0;i<A.size();i++)
            for(int j = 0;j<B.size();j++)
                if(A[i] == B[j])
                    dp[i+1][j+1] = dp[i][j]+1;
                else
                    dp[i+1][j+1] = max(dp[i+1][j],dp[i][j+1]);
        return dp[A.size()][B.size()];
    }
};
```
