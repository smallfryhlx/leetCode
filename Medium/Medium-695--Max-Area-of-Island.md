[https://leetcode.com/problems/max-area-of-island/](https://leetcode.com/problems/max-area-of-island/)
//深度优先搜索
```
class Solution {
public:
    int maxAreaOfIsland(vector<vector<int>>& grid)
    {
        int max = 0;
        for(int i = 0; i < grid.size(); i++)
            for(int j = 0 ; j < grid[0].size();j++)
            {
                if(grid[i][j] == 1)
                {
                    int area = 0;
                    find(grid,i,j,area);
                    if(max < area)
                        max = area;
                }
            }
        return max;
    }

private:
    void find(vector<vector<int>>& grid,int i,int j,int &area)
    {
        if(0<=i && i < grid.size() && 0<=j && j < grid[0].size())
        {
            if(grid[i][j] == 1)
            {
                grid[i][j] = 0;
                area++;
                find(grid,i-1,j,area);
                find(grid,i+1,j,area);
                find(grid,i,j+1,area);
                find(grid,i,j-1,area);
            }
        }
    }
};
```
