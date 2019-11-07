求数组的循环的最大长度
```
class Solution {
public:
    int arrayNesting(vector<int>& nums) {
        bitset<20000> s;
        int longest = INT32_MIN;
        for(int i = 0;i < nums.size();i++)
        {
            if(!s[i]){
                s.set(i,1);
                int index = nums[i];
                int cnt = 1;
                while(index != i)
                {
                    cnt++;
                    s.set(index,1);
                    index = nums[index];
                }
                if(longest < cnt)
                    longest = cnt;
            }
        }
        return longest;
    }
};
```
