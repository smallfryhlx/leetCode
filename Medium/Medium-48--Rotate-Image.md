数组翻转  翻转两次即可
```
class Solution {
public:
    void rotate(vector<vector<int>>& matrix) {
        for(int i = 0; i < matrix.size()/2;i++)
            for(int j = 0;j<matrix[0].size();j++)
                swap(matrix[i][j],matrix[matrix.size()-1-i][j]);
        for(int i = 0; i < matrix.size();i++)
            for(int j = i+1;j<matrix[i].size();j++)
                swap(matrix[i][j],matrix[j][i]);
    }
};
```
