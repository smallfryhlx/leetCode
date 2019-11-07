插花问题 花不能相邻，必须间隔
Runtime: 16 ms, faster than 83.09%
Memory Usage: 10 MB, less than 100.00% 
就是赋值呗
```
class Solution {
public:
    bool canPlaceFlowers(vector<int>& flowerbed, int n) {
        auto len = static_cast<int>(flowerbed.size());
        if(n == 0)
            return true;
        if(len <= 1)
        {
            return flowerbed[0]==1? false:n==1;
        }
        for(int i = 0;i < len;i++)
        {
            if(IsSuccess(flowerbed, len, i))
            {
                n--;
                if(n==0)
                    return true;
            }
        }
        return false;
    }
private:
    bool IsSuccess(vector<int>& flowerbed, int size,int pos)
    {
        if(flowerbed[pos] == 1)
            return false;
        if(pos == 0)
        {
            if(flowerbed[1] == 1)
            {
                return false;
            }else{
                flowerbed[0] = 1;
                return true;
            }
        }
        if(pos == (size -1))
        {
            if(flowerbed[pos-1] == 1)
            {
                return false;
            }else{
                flowerbed[pos-1] = 1;
                return true;
            }
        }
        if(flowerbed[pos-1] == 0 && flowerbed[pos+1] == 0)
        {
            flowerbed[pos] = 1;
            return true;
        }
        return false;
    }
};
```
