[https://leetcode.com/problems/flip-string-to-monotone-increasing/](https://leetcode.com/problems/flip-string-to-monotone-increasing/)
把01字符串翻转成 0···1···的形式 遍历一下就行了
```
class Solution {
public:
    int minFlipsMonoIncr(string S) {
        int flip_0_1 = 0;
        int zero_cnt = 0;
        int one_cnt = 0;
        for(auto ch : S)
            if(ch == '0')
                zero_cnt++;
        int change_times_1_0 = 0;
        int flips_0_1 = zero_cnt;
        for(auto ch : S)
        {
            if(ch == '0')
            {
                zero_cnt--;
            }else{
                change_times_1_0++;
            }
            auto flip = zero_cnt+change_times_1_0;
            if(flips_0_1 > flip)
                flips_0_1 = flip;
        }
        return flips_0_1;
    }
};
```
