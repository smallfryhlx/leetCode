找出一样的数字位置差距是否最多为k
[https://leetcode.com/problems/contains-duplicate-ii/](https://leetcode.com/problems/contains-duplicate-ii/)
Runtime: 40 ms, faster than 30.43% 
Memory Usage: 15.3 MB, less than 82.35%
```
class Solution {
public:
    bool containsNearbyDuplicate(vector<int>& nums, int k) {
        int len = nums.size();
        if(len <= 1)
            return false;
        std::map<int,std::pair<int,int>> m;
        for(int i = 0;i < len;i++)
        {
            auto &val = m[nums[i]];
            auto & a =  std::get<0>(val);
            auto &cnt = std::get<1>(val);
            if(cnt < 2)
                cnt++;
            if(cnt == 2)
            {
                if((i-a) <= k)
                    return true;
            }
            a = i;
        }
        return false;
    }
};
```
