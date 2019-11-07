判断一个字符串扩展后是否是另一个字符串，扩展只能重复字符本身
Runtime: 4 ms, faster than 60.21% 
Memory Usage: 8.7 MB, less than 14.29%
```
class Solution {
public:
    bool isLongPressedName(string name, string typed) {
        int len1 = name.size();
        int len2 = typed.size();
        int cmp_index = 0;
        int cmp_cnt = 0;
        int j_cnt = 0;
        int j = 0;
        while (cmp_index < len1 && j < len2)
        {
            while(cmp_index < (len1 -1) && name[cmp_index] == name[cmp_index+1])
            {
                cmp_index++;
                cmp_cnt++;
            }
            while(j < (len2-1)  && typed[j] == typed[j+1])
            {
                j++;
                j_cnt++;
            }
            if(name[cmp_index] != typed[j])
                return false;
            if(cmp_cnt > j_cnt)
                return false;
            cmp_cnt = 0;
            j_cnt = 0;
            cmp_index++;
            j++;
        }
        return cmp_index == len1;
    }
};
```
