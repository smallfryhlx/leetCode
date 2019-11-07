交换两个字符串中的两个位置的字母，使得两个字符串相等。
Runtime: 4 ms, faster than 98.65%
Memory Usage: 9.1 MB, less than 100.00%
####实现代码
```
class Solution {
public:
    bool buddyStrings(string A, string B) {
        int len1 = A.length();
        int len2 = B.length();

        if(len1 != len2)
            return false;
        int cnt = 0;
        int i = 0;
        char swap1[2];
        char swap2[2];
        while(i < len1)
        {
            if(A[i] != B[i])
            {
                if(cnt == 2)
                    return false;
                swap1[cnt] = A[i];
                swap2[cnt] = B[i];
                cnt++;
            }
            i++;
        }
        if(cnt == 0)
            return hasSameLetter(A);
        if(cnt == 1)
            return false;
        if(cnt == 2)
            return swap1[0] == swap2[1] && swap1[1] == swap2[0];
        return false;
    }
    bool hasSameLetter(string& s)
    {
        std::set<char> set1;
        for(auto ch : s)
        {
            auto ret = set1.insert(ch);
            if(!ret.second){
                return true;
            }
        }
        return false;
    }
};
```
