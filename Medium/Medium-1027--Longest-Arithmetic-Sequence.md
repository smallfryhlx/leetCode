[https://leetcode.com/problems/longest-arithmetic-sequence/](https://leetcode.com/problems/longest-arithmetic-sequence/)
```
class Solution {
public:
    int longestArithSeqLength(vector<int>& A) {
        int ret = 0;
        for(int i = 0;i<A.size();i++)
        {
            for(int j = i+1;j<A.size();j++)
            {
                int a = A[i];
                int b = A[j];
                int delta = b - a;
                int k = j+1;
                a = b;
                int cnt = 2;
                while(k < A.size())
                {
                    if((A[k] - a) == delta)
                    {
                        a = A[k];
                        cnt++;
                    }
                    k++;
                }
                if(ret < cnt)
                    ret = cnt;
            }
        }
        return ret;
    }
};

```
