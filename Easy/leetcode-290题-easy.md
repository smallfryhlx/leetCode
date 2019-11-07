正则
Runtime: 4 ms, faster than 56.07% 
Memory Usage: 8.4 MB, less than 100.00%
[https://leetcode.com/problems/word-pattern/](https://leetcode.com/problems/word-pattern/)
26个字母 相同的字母对应的字符串记录下来，然后比较后面遇到相同字母对应的字符串
```
class Solution {
public:
    bool wordPattern(string pattern, string str)
    {
       int len_pattern = pattern.length();
       int len_str = str.length();
       string arr[26]={};
       for(int i = 0;i<26;i++)
       {
           arr[i] = "";
       }
       int i = 0;
       int j = 0;
       std::string s = "";
       bool start = false;
       bool end = false;
       while(i < len_pattern && j < len_str)
       {
           if(j==(len_str-1))
           {
               if(str[j] != ' ')
               {
                   s += str[j];
               }
               end = true;
           }else{
               if(str[j] != ' ' && !start)
               {
                   start = true;
                   s += str[j];
               }else if(str[j] != ' ' && start){
                   s += str[j];
               }else if(str[j] == ' ' && start){
                   end = true;
                   start = false;
               }
           }
           if(end)
           {
               end = false;
               start = false;
               //std::cout<<pattern[i]<<std::endl;
               //std::cout<<s<<std::endl;
               if(arr[pattern[i] - 'a'].length() == 0){
                   arr[pattern[i] - 'a'] = s;
               }else{
                   if(arr[pattern[i] - 'a'] != s){
                       return false;
                   }
               }
               i++;
               s= "";
           }
           j++;
       }
       if(i != len_pattern)
           return false;
       while(j < len_str)
       {
           if(str[j++]!= ' ')
               return false;
       }
       for(int m = 0;m<26;m++)
       {
           if(arr[m].length() == 0)
               continue;
           for(int n = m+1;n<26;n++)
           {
               if(arr[n].length() == 0)
                   continue;
               if(arr[i] == arr[j])
                   return false;
           }
       }
       return true;
    }
};
```
