[https://leetcode.com/problems/total-hamming-distance/](https://leetcode.com/problems/total-hamming-distance/)

//求一组数相互之间的汉明距离之和
//主要是一个int有32位 每一位单独拿出来比较，看看N个数中 第i位的汉明距离之和
```
class Solution {
public:
    int totalHammingDistance(vector<int>& nums) {
        vector<int> help(32,0);
        for(auto &num :nums)
        {
            int i = 0;
            while(i < 32)
            {
                if(num & (1<<i))
                    help[i]++;
                i++;
            }
        }
        int len = nums.size();
        int ans = 0;
        for(auto h : help)
            ans += h *(len-h);
        return ans;
    }
};
```
