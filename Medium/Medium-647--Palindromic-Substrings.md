[https://leetcode.com/problems/palindromic-substrings/](https://leetcode.com/problems/palindromic-substrings/)
//回文只能是aba abba类型 遍历即可
```
class Solution {
public:
    int countSubstrings(string s) {
        int len = s.length();
        int ans = 0;
        for(int i = 0; i < len ;i++)
        {
            ans += getSingelCenterLen(s,len,i) + getDoubleCenterLen(s,len,i);
        }
        return ans;
    }

private:
    int getSingelCenterLen(string &s,int len,int index)
    {
        int center = index;
        int cnt = 0;
        int left = center;
        int right = center;
        while(left>=0 && right < len)
        {
            if(s[left] == s[right])
                cnt++;
            else
                return cnt;
            left--;
            right++;
        }
        return cnt;
    }
    int getDoubleCenterLen(string &s,int len,int index)
    {
        int left = index;
        int right = index+1;
        int cnt = 0;
        while (left>=0 && right < len)
        {
            if(s[left] == s[right])
                cnt++;
            else
                return cnt;
            left--;
            right++;
        }
        return cnt;
    }
};
```
