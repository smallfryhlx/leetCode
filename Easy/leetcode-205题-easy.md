同构字符串 转换成一个字符串即可
Runtime: 8 ms, faster than 86.64% of C++ online submissions for Isomorphic Strings.
Memory Usage: 9.2 MB, less than 70.00% of C++ online submissions for Isomorphic Strings.
[https://leetcode.com/problems/isomorphic-strings/](https://leetcode.com/problems/isomorphic-strings/)
```
class Solution {
public:
    bool isIsomorphic(string s, string t) {
        int len = s.length();
        char base[226]={};
        char cast2ch=1;
        for(int i = 0;i<len ;i++)
        {
            if(base[s[i]] == 0)
            {
                base[s[i]] = cast2ch;
                cast2ch++;
            }
            s[i] = base[s[i]];
        }
        char baset[26]={};
        cast2ch=1;
        for(int i = 0 ; i <len;i++)
        {
            if(baset[t[i]] == 0)
            {
                baset[t[i]] = cast2ch;
                cast2ch++;
            }
            t[i] = baset[t[i]];
        }
        return s == t;
    }
};
```
