
```
class Solution {
public:
    vector<vector<int>> generateMatrix(int n) {
        vector<vector<int>> ans(n,vector<int>(n,0));
        int left = 0;
        int up = 0;
        int right = n-1;
        int down = n-1;
        int val = 1;
        while(left <= right && up <= down)
        {
            for(int i =left ; i <= right; i++)
                ans[i][up] = val++;
            up++;
            for(int j = up;j<=down;j++)
                ans[right][j] = val++;
            right--;
            for(int i = right;i>=left;i--)
                ans[i][down] = val++;
            down--;
            for(int j = down;j>=up;j--)
                ans[left][j] = val++;
            left++;
        }
        vector<vector<int>> ans1(n,vector<int>(n,0));
        for(int j = 0;j < n;j++)
            for(int i = 0;i<n;i++)
                ans1[i][j] = ans[j][i];
        return ans1;
    }
};

```
