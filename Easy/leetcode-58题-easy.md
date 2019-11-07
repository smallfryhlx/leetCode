找出字符串最后一个连续字符的长度
Runtime: 4 ms, faster than 71.52%
Memory Usage: 8.7 MB, less than 86.11% 
从后往前找，找到连续字符的开始跟结束位置即可
```
class Solution {
public:
    int lengthOfLastWord(string s) {
        bool begin = false;//找到word开头 倒序
        int begin_intdex = -1;
        int len = s.length();
        for(int i = len-1;i >= 0;i--)
        {
            if(s[i] == ' ' || i==0)
            {
                if(!begin){
                    if(i==0){
                        if(s[i] == ' '){
                            return 0;
                        }
                        return 1;
                    }
                    continue;
                }else{
                    if(i==0)
                    {
                        if(s[0] == ' ')
                        {
                            return begin_intdex;
                        }
                        return begin_intdex+1;
                    }
                    return begin_intdex - i;
                }
            }else{
                if(!begin){
                    begin = true;
                    begin_intdex = i;
                    std::cout<<begin_intdex<<std::endl;
                }
            }
        }
        return 0;
    }
};
```
