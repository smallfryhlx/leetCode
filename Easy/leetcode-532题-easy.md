数组中差值为k的对数。
Runtime: 48 ms, faster than 27.52%
Memory Usage: 13.9 MB, less than 18.18% 
[https://leetcode.com/problems/k-diff-pairs-in-an-array/](https://leetcode.com/problems/k-diff-pairs-in-an-array/)
####实现代码
不知道为什么bitmap没有STl 中的sort快？？
```
class Solution {
public:
    //找出数组中差值为k的对数
    int findPairs(vector<int>& nums, int k)
    {
       int len = nums.size();
       int cnt = 0;
       if(len <= 1)
           return 0;
       auto min_max = findMax(nums,len);
       int diff_len = min_max.second - min_max.first + 1;
       if(k < 0)
           return 0;
       if((min_max.second - min_max.first) < k )
           return 0;
        if(k == 0)
        {
            int8_t arr[(diff_len+k)/8+1]={0};
            int8_t appeartimes2[(diff_len+k)/8+1]={0};
            int8_t counted[(diff_len+k)/8+1]={0};
            for(auto &num : nums)
            {
                num -= min_max.first;//全部变为非负数
                if(getBit(arr,num))
                {
                    setBit(appeartimes2,num,1);//出现两次以上了
                }else{
                    setBit(arr,num,1);
                }
            }
            int max_k = min_max.second - min_max.first - k;
            for(auto &num : nums)
            {
                if(!getBit(counted,num) && getBit(appeartimes2,num))
                {
                    cnt++;
                    setBit(counted,num,1);//已经找过了
                }
            }
            return cnt;
       }
       int8_t bits[(diff_len+k)/8+1]={0};
       int8_t counted[(diff_len+k)/8+1]={0};
       for(auto &num : nums)
       {
           num -= min_max.first;//全部变为非负数
           setBit(bits,num,1);
       }
       int max_k = min_max.second - min_max.first - k ;
       for(auto &num :nums)
       {
           if(!getBit(counted,num) && getBit(bits,num+k))
           {
               cnt++;
               setBit(counted,num,1);//已经找过了
           }
       }
       return cnt;
    }
private:
    void setBit(int8_t bits[],int index,int flag)
    {
        int a = index/8;
        int b = index %8;
        bits[a] |= flag<<b;
    }
    int getBit(int8_t bits[],int index)
    {
        int a = index/8;
        int b = index %8;
        return (bits[a] >> b) &1;
    }
    std::pair<int,int> findMax(vector<int> &nums,int len)
    {
        int max = nums[0];
        int min = nums[0];
        for(int i= 1; i<len;i++)
        {
            if(nums[i] >max)
            {
                max = nums[i];
            }
            if(nums[i] < min)
            {
                min = nums[i];
            }
        }
        return std::make_pair(min,max);
    }
};
```
