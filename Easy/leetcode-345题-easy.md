只逆序元音字母
Runtime: 8 ms, faster than 92.95% 
Memory Usage: 10.1 MB, less than 69.70%
```
class Solution {
public:
    string reverseVowels(string s) {
        int len = s.length();
        int begin = 0;
        int end = len - 1;
        if(len <= 1)
            return s;

        while(begin < end)
        {
            if(!isVol(s[begin]) || !isVol(s[end]))
            {
                if(!isVol(s[begin]))
                {
                    begin++;
                }
                if(!isVol(s[end]))
                {
                    end--;
                }
            }else{
                std::swap(s[begin],s[end]);
                begin++;
                end--;
            }
        }
        return s;
    }
private:
    bool isVol(char ch)
    {
        return ch == 'a' || ch == 'e' || ch == 'i' || ch == 'o'
               || ch == 'u' ||ch == 'A' || ch == 'E' ||
               ch == 'I' || ch == 'O' || ch == 'U';
    }
};
```
