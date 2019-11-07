暴躁书店老板
老板暴躁的时候顾客就不爽，但是老板每天有一次控制暴躁的机会，求使得顾客满意的最大人数
[https://leetcode.com/problems/grumpy-bookstore-owner/](https://leetcode.com/problems/grumpy-bookstore-owner/)

```
class Solution {
public:
    int maxSatisfied(vector<int>& customers, vector<int>& grumpy, int X) {

        int cnt = 0;
        for(int i = 0;i<grumpy.size();i++)
        {
            cout<<grumpy[i]<<endl;
            if(grumpy[i] == 0)
            {
                cnt += customers[i];
            }
        }
        int j = 0;
        int countUseX = 0;
        for(;j<X && j < customers.size() ;j++)
            if(grumpy[j] == 1)
                countUseX+=customers[j];
        int first = 0;
        int last = X-1;
        int maxCountUseX = countUseX;
        while((last+1) < customers.size())
        {
            if(grumpy[first] == 1)
                countUseX -= customers[first];
            if(grumpy[last+1] ==1)
                countUseX += customers[last+1];
            if(maxCountUseX < countUseX)
                maxCountUseX = countUseX;
            last++;
            first++;
        }
        return cnt + maxCountUseX;
    }
};
```
