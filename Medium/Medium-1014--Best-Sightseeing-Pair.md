求 A[i]+i+A[j]-j的最大值
3O(N)居然这么慢
```
class Solution {
public:
    int maxScoreSightseeingPair(vector<int>& A)
    {
        int max = INT32_MIN;
        vector<int> beforeMax(A.size()-1,0);
        vector<int> afterMax(A.size()-1,0);
        int before = A[0]+0;
        for(int i = 0;i<A.size()-1;i++)
        {
            if((A[i]+i) > before)
                before = A[i]+i;
            beforeMax[i] = before;
        }
        int after = A[A.size()-1] - (A.size()-1);
        for(int j = A.size()-2;j>=0;j--)
        {
            afterMax[j] = after;
            if(after < (A[j]-j))
                after = A[j]-j;
        }
        for(int i = 0 ; i < beforeMax.size();i++)
            if(max < (beforeMax[i] + afterMax[i]))
                max = (beforeMax[i] + afterMax[i]);
        return max;
    }
};
```
