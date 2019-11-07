把手里的牌分成几组连续的数字，利用map
[https://leetcode.com/problems/hand-of-straights/](https://leetcode.com/problems/hand-of-straights/)
Runtime: 72 ms, faster than 91.11% of C++ online submissions for Hand of Straights.
Memory Usage: 17.5 MB, less than 66.67% of C++ online submissions for Hand of Straights.
```
class Solution {
public:
    bool isNStraightHand(vector<int>& hand, int W) {
        int len = hand.size();
        if(len % W != 0)
            return false;
        map<int,int> help;
        for(auto &num : hand)
            help[num]++;
        while(!help.empty())
        {
            auto it = help.begin();
            int min = it->first;
            int i = 0;
           for(;it != help.end() && i < W;){
                int findNum = min + i;
                cout<<min<<":"<<i<<":"<<it->first<<endl;
                if(findNum != it->first)
                    return false;
                if(0 == --it->second )
                {
                    it = help.erase(it);
                }else{
                    it++;
                }
                i++;
                cout<<"i="<<i<<endl;
            }
            if(i != W)
                return false;
        }
        return true;
    }
};

```
