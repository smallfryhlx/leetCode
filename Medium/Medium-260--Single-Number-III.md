[https://leetcode.com/problems/single-number-iii/](https://leetcode.com/problems/single-number-iii/)
//一组数其中两个数出现一次，其他数每个都出现两次
//利用到 与或运算 两个数不同的数 某一位与或后为1就可以区分这俩数
```
class Solution {
public:
    vector<int> singleNumber(vector<int>& nums) {
        int x = 0;
        for(auto &num :nums)
            x ^= num;
        int flag = 0;
        for(int i = 0;i<=31;i++)
        {
            if( ((1 << i) & x) != 0)
            {
                flag = (1<<i);
                break;
            }
        }
        int a = 0;
        int b = 0;
        for(auto &num:nums)
        {
            if(num & flag)
            {
                a ^= num;
            }else{
                b^=num;
            }
        }
        vector<int> ans{a,b};
        return ans;
    }
};
```
