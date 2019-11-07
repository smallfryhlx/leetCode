Runtime: 116 ms, faster than 60.23% 
Memory Usage: 13.6 MB, less than 44.44% 
[https://leetcode.com/problems/add-to-array-form-of-integer/](https://leetcode.com/problems/add-to-array-form-of-integer/)
相当于两个数相加
```
class Solution {
public:
    vector<int> addToArrayForm(vector<int>& A, int K) {
        bool flag = false;
        int len = A.size();
        int i = len - 1;
        vector<int> v;
        while(i>=0 && K > 0)
        {
            int num = K % 10;
            int sum = A[i] + num;
            if(flag){
                sum += 1;
            }
            v.push_back(sum % 10);
            flag = (sum / 10 == 1);
            i--;
            K = K / 10;
        }
        while(i>=0)
        {
            int sum = A[i];
            if(flag)
                sum+=1;
            v.push_back(sum % 10);
            flag = (sum / 10 == 1);
            i--;
        }
        while(K > 0)
        {
            int sum =K % 10;
            if(flag)
                sum+=1;
            v.push_back(sum % 10);
            flag = (sum / 10 == 1);
            K = K / 10;
        }
        if(flag)
            v.push_back(1);
        int lenv = v.size();
        for(int k = 0;k<lenv/2;k++)
        {
            swap(v[k],v[lenv-1-k]);
        }
        return v;
    }
};
```
