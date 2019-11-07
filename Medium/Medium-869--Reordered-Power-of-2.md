一个数能不能通过变换数字的位置  变为2的幂次方
32个幂次数都比较一遍
```
class Solution {
public:
    bool reorderedPowerOf2(int N) {
        map<int,int> m;
        while(N)
        {
            auto a = N % 10;
            m[a]++;
            N /= 10;
        }

        for(int i = 0; i <= 31; i++)
        {
            int num = 1<<i;
            if(canCombin(num,m))
                return true;
        }

        return false;
    }

private:
    bool canCombin(int target,map<int,int> nums)
    {
        while(target)
        {
            auto a = target % 10;
            auto it = nums.find(a);
            if(it == nums.end()){
                return  false;
            }else{
                if(--it->second == 0)
                {
                    nums.erase(it);
                }
            }
            target /= 10;
        }
        return nums.empty();
    }
};
```
