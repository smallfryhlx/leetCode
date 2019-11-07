字符串表示的二进制相加
Runtime: 0 ms, faster than 100.00%
Memory Usage: 8.6 MB, less than 83.64%
[https://leetcode.com/problems/add-binary/](https://leetcode.com/problems/add-binary/)
```
class Solution {
public:
    string addBinary(string a, string b) {
        int lena = a.length();
        int lenb = b.length();
        reverse(a,lena);
        reverse(b,lenb);
        string s;
        int i = 0;int j= 0;
        bool overflow = false;
        while(i<lena && j < lenb)
        {
            int ai = a[i]-'0';
            int bj = b[j]-'0';
            int sum = ai + bj;
            if(overflow){
                if(sum == 2)
                {
                    s+="1";
                }else if(sum == 0){
                    s += "1";
                    overflow = false;
                }else{
                    s += "0";
                }
            }else{
                if(sum == 2)
                {
                    s += "0";
                    overflow = true;
                }else if(sum == 0){
                    s += "0";
                }else{
                    s += "1";
                }
            }
            i++;j++;
        }
        cout<<i<<":"<<j<<":"<<overflow<<endl;
        while(i < lena)
        {
            if(overflow){
                if(a[i] == '1'){
                    s += "0";
                }else{
                    s += "1";
                    overflow = false;
                }
            }else{
                s += a[i];
            }
            i++;
        }

        while(j < lenb)
        {
            if(overflow){
                if(b[j] == '1'){
                    s += "0";
                }else{
                    s += "1";
                    overflow = false;
                }
            }else{
                s += b[j];
            }
            j++;
        }
        if(overflow)
            s += "1";
        reverse(s,s.length());
        return s;
    }
private:
    void reverse(string &a,int len)
    {
        for(int i = 0;i<len/2;i++)
        {
            swap(a[i],a[len-1-i]);
        }
    }
};
```
