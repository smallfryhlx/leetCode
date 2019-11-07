压缩char数组
Runtime: 8 ms, faster than 84.64% 
Memory Usage: 9.1 MB, less than 100.00%
[https://leetcode.com/problems/string-compression/](https://leetcode.com/problems/string-compression/)
考虑问题要全面，关键在于边边角角
```
class Solution {
public:
    int compress(vector<char>& chars) {
        int len = chars.size();
        if(len <= 1)
            return 1;
        char begin_ch = chars[0];
        int size = 1;
        int i = 1;
        int k = 0;
        while(i < len)
        {
            if(i == len-1)
            {
                if(begin_ch == chars[i])
                {
                    chars[k++] = begin_ch;
                    size++;
                    if(size > 1)
                    {
                        auto s = to_string(size);
                        for(auto ch : s)
                        {
                            chars[k++] = ch;
                        }
                    }
                }else{
                    chars[k++] = begin_ch;
                    if(size > 1)
                    {
                        auto s = to_string(size);
                        for(auto ch : s)
                        {
                            chars[k++] = ch;
                        }
                    }
                    chars[k++] = chars[i];
                }
            }else{
                if(begin_ch == chars[i])
                {
                    size++;
                }else{
                    chars[k++] = begin_ch;
                    if(size > 1)
                    {
                        auto s = to_string(size);
                        for(auto ch : s)
                        {
                            chars[k++] = ch;
                        }
                    }
                    begin_ch = chars[i];
                    size = 1;
                }
            }
            i++;
        }
        return k;
    }
};
```
