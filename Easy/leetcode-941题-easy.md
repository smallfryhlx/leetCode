山形数组
Runtime: 36 ms, faster than 78.97%
Memory Usage: 10.3 MB, less than 100.00%
[https://leetcode.com/problems/valid-mountain-array/](https://leetcode.com/problems/valid-mountain-array/)
```
bool validMountainArray(vector<int>& A) {
        int len = A.size();
        if(len < 3)
            return false;
        int desc_begin = -1;
        int max = -1;
        for(int i = 0;i< len - 1;i++)
        {
            if((A[i] > A[i+1]))
            {
                desc_begin = i;
                break;
            }else if(A[i] == A[i+1])
                return false;
        }
        if(desc_begin == 0 || desc_begin == -1)
        {
            return false;
        }
        std::cout<<A[desc_begin]<<std::endl;
        for(int j = desc_begin;j<len-1;j++)
        {
            if(A[j] <= A[j+1])
            {
                return false;
            }
        }
        return true;
    }
```
