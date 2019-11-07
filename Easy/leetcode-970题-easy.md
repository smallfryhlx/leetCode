求解x^j+y^i 小于bound的所有值
Runtime: 4 ms, faster than 59.56%
Memory Usage: 8.3 MB, less than 100.00%
首先求到 i,j的上限然后遍历添加数据
```
class Solution {
public:
    vector<int> powerfulIntegers(int x, int y, int bound) {
        vector<int> ret;
        if(bound < 2)
            return ret;
        int k = x > y ? y:x;
        if(x == 1)
            k = y;
        if(y == 1)
            k = x;
        int n = bound/2;
        int max = 0;
        if(k == 1)
        {
            if(bound >= 2)
            {
                ret.emplace_back(2);
                return ret;
            }
        }
        while(n)
        {
            n /=k;
            max++;
        }
        cout<<max<<endl;
        for(int i = 0;i<=max;i++)
        {
            auto numi = powerN(x,i);
            for(int j = 0;j<=max;j++)
            {
                auto numj = powerN(y,j);
                auto sum = numi+numj;
                if(sum > bound)
                    break;
                if(!Hash(ret,sum))
                    ret.emplace_back(sum);
            }
        }
        sort(ret.begin(),ret.end());
        return ret;
    }
private:
    int powerN(int i ,int n)
    {
        int cnt = 1;
        for(int j = 0;j<n;j++)
            cnt*=i;
        return cnt;
    }
    bool Hash(vector<int> &v,int find)
    {
        for(auto item : v)
        {
            if(item == find)
                return true;
        }
        return false;
    }
};
```
