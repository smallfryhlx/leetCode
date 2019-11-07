把数字转化为A-Z的字符串，其中1代表A，26代表Z，以此类推。
Runtime: 0 ms, faster than 100.00%
Memory Usage: 8 MB, less than 100.00%
[https://leetcode.com/problems/excel-sheet-column-title/](https://leetcode.com/problems/excel-sheet-column-title/)
***string的push_back函数效率低下，不如使用 str1 += str2效率高！***
####代码实现
```
class Solution {
public:
    //1-A 2-B
    string convertToTitle(int n) {
        int a = n;
        std::string s;
        int len = 0;
        int b = 0;
        while(a)
        {
            b = a % 26;
            if(b == 0)
            {
                s += 'Z';
                a -= 26;
            }else{
                s +=char(b+'A'-1);
            }
            a /= 26;
            len++;
        }
        for(int i = 0;i<len/2;i++)
        {
            std::swap(s[i],s[len-1-i]);
        }
        return s;
    }
};
```
