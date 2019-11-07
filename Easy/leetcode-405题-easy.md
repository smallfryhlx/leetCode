吧三十二字节的有符号数转换为16进制
Runtime: 0 ms, faster than 100.00% 
Memory Usage: 8.1 MB, less than 100.00%
[https://leetcode.com/problems/convert-a-number-to-hexadecimal/](https://leetcode.com/problems/convert-a-number-to-hexadecimal/)
主要是考虑对于负数需要设置向右移的次数不能超过八次
```
class Solution {
public:
    string toHex(int num) {
        string s;
        if(num == 0)
            return 0;
        string arr[16]={"1","2","3","4","5","6","7","8","9","a","b","c","d","e","f","0"};
        int i = 0;
        while(num && i < 8)
        {
            int tmp  = num & 0xf;
            s += arr[(16 + tmp - 1) % 16];
            num =num >> 4;
            i++;
        }
        int len = s.length();
        for(int i = 0 ; i < len/2; i++)
        {
            swap(s[i],s[len-1-i]);
        }
        return s;
    }
};
```
