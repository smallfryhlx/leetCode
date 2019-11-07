字符串是由一个字符串复制n次形成的吗
Runtime: 32 ms, faster than 76.97% 
Memory Usage: 12.7 MB, less than 85.71% 
[https://leetcode.com/problems/repeated-substring-pattern/](https://leetcode.com/problems/repeated-substring-pattern/)

主要就是将一个数的所有可能的整除数都找出来
```
class Solution {
public:
    bool repeatedSubstringPattern(string s) {
        auto len = static_cast<int>(s.length());
        if(len == 1)
            return false;
        auto k = static_cast<int>(std::sqrt(len));
        for(int num = 1;num <= k;num++)
        {
            if(len % num == 0)
            {
                int len1 = num;
                if(isSubNTimes(s,len,s.substr(0,len1),len1))
                   return true;
                
                int len2 = len / num;
                if(len1 != len2 && len1 != 1)
                    if(isSubNTimes(s,len,s.substr(0,len2),len2))
                        return true;
            }
        }
        return false;
    }
private:
    bool isSubNTimes(string&s,int len, const string &pattern,int lenp)
    {
        int i = lenp;
        int j = 0;
        while(i<len && j < lenp)
        {

            if(s[i] != pattern[j])
                return false;
            i++;
            j++;
            if(j == lenp)
                j=0;
        }
        return true;
    }
};
```
