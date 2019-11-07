去掉一个字符 字符串是回文吗
Runtime: 96 ms, faster than 94.54%
Memory Usage: 21.8 MB, less than 63.64%
利用  begin  end 遍历比较有时候更容易操作
```
class Solution {
public:
    bool validPalindrome(string s) {
        int del_index_1 = -1;
        int del_index_2 = -1;
        auto len = static_cast<int>(s.length());
        int begin = 0;
        int end = len-1;
        bool ret = true;
        bool del_one = false;
        while(begin < end)
        {
            if(s[begin] == s[end])
            {
                begin++;
                end--;
            }else{
                if(del_one)
                {
                   ret = false; 
                   break; 
                }else{
                    begin++;
                    del_one = true;
                }
            }
        }
        if(!ret){
            begin = 0;
            end = len-1;
            ret = false;
            del_one = false;
            while(begin < end)
            {
                if(s[begin] == s[end])
                {
                    begin++;
                    end--;
                }else{
                    if(del_one)
                    {
                        return false;
                    }else{
                        end--;
                        del_one = true;
                    }
                }
            }
        }
        return true;
    }
};
```
