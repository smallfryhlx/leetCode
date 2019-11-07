找出字符串数组前段最长的相同子字符串。
Runtime: 4 ms, faster than 94.84%
Memory Usage: 8.9 MB, less than 45.16%
遍历
```
class Solution {
public:
    string longestCommonPrefix(vector<string>& strs) {
        int i = 0;
        std::string prefix = "";
        int len = strs.size();
        if(len == 0)
            return prefix;
        std::string first = strs[0];
        int str_size[len] = {0};
        for(int j = 0;j< len; j++)
        {
            str_size[j] = strs[j].size();
        }
        while(len != 0)
        {
            for(int j = 0;j< len; j++)
            {
                if(i < str_size[j])
                {
                    if(first[i] != strs[j][i])
                    {
                        return prefix;
                    }
                }else{
                    return prefix;
                }
            }
            prefix += first[i];
            i++;
        }
        return prefix;
    }
};
```
