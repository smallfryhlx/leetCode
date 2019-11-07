字符串中的数字跟字母是否为回文
Runtime: 8 ms, faster than 83.81%
Memory Usage: 9.3 MB, less than 89.80%
[https://leetcode.com/problems/valid-palindrome/](https://leetcode.com/problems/valid-palindrome/)

####实现代码
```
class Solution {
public:
    bool isPalindrome(string s) {
        int begin = 0;
        int end = s.length() - 1;
        bool findOnePair = false;
        while(begin < end)
        {
            if(IsChar(s[begin]) && IsChar(s[end]))
            {
                if(tolower(s[begin]) != tolower(s[end]))
                {
                    return false;
                }
                begin++;
                end--;
            }else if(!IsChar(s[begin]) && IsChar(s[end]))
            {
                begin++;
            } else if(IsChar(s[begin]) && !IsChar(s[end])){
                end--;
            }else{
                begin++;
                end--;
            }
        }
        return true;
    }
private:
    bool IsChar(char ch)
    {
        return ('A'<=ch&&ch<='Z') || ('a'<=ch&&ch<='z') || ('0' <= ch && ch <= '9');
    }
};
```
