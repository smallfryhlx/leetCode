两个字符串化成数字相加返回相加后的字符串
Runtime: 4 ms, faster than 92.04% of C++ online submissions for Add Strings.
Memory Usage: 9.2 MB, less than 39.13% of C++ online submissions for Add Strings.
```
class Solution {
public:
    string addStrings(string num1, string num2) {
        bool flag = false;
        int len1 = num1.size();
        int len2 = num2.size();
        int i = len1-1;
        int j = len2-1;
        string s;
        while(i>=0 && j>=0)
        {
            int sum = num1[i] -'0' + num2[j] - '0';
            if(flag)
                sum += 1;
            s += to_string(sum%10);
            flag = sum / 10 == 1;
            i--;
            j--;
        }
        while(i>=0)
        {
            int sum = num1[i] -'0';
            if(flag)
                sum += 1;
            s += to_string(sum%10);
            flag = sum / 10 == 1;
            i--;
        }
        while(j>=0)
        {
            int sum =num2[j] - '0';
            if(flag)
                sum += 1;
            s += to_string(sum%10);
            flag = sum / 10 == 1;
            j--;
        }
        if(flag)
            s += '1';
        int len = s.size();
        for(int k = 0;k<len/2;k++)
            swap(s[k],s[len-k-1]);
        return s;
    }
};
```
