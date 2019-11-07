知道1-n的数组中重复的那个数字 并且缺少的那个数字
Runtime: 36 ms, faster than 85.91% of C++ online submissions for Set Mismatch.
Memory Usage: 10.5 MB, less than 50.00% of C++ online submissions for Set Mismatch.
[https://leetcode.com/problems/set-mismatch/](https://leetcode.com/problems/set-mismatch/)
利用了一个bitmap
```
class Solution {
public:
    vector<int> findErrorNums(vector<int>& nums) {
        auto len = static_cast<int>(nums.size());
        uint8_t  arr[len/8+1]={};
        int find = -1;
        int count = 0;
        for(int i = 0;i < len;i++)
        {
            if(find == -1)
            {
                if(getBit(arr,nums[i]))
                {
                    find = nums[i];
                }else{
                    setBit(arr,nums[i]);
                }
            }
            count += nums[i];
        }
        int need = len*(1+len)/2 -(count - find);
        return {find,need};
    }

private:
    void setBit(uint8_t arr[],int index)
    {
        int a = index % 8;
        int b = index / 8;
        arr[b] |= 1<<a;
    }
    bool getBit(uint8_t arr[],int index)
    {
        int a = index % 8;
        int b = index / 8;
        return (arr[b] >> a)&1;
    }
};
```
