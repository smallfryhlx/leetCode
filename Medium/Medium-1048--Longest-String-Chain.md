Runtime: 68 ms, faster than 76.10% of C++
Memory Usage: 12.8 MB, less than 100.00% of C++
```
class Solution {
public:
    int longestStrChain(vector<string>& words) {
        vector<vector<int>> help(words.size(),vector<int>(0,0));
        //help[i] 表示 words[i] 属于最靠近words[i]长度的母字符串
        sort(words.begin(),words.end(),[](string &a,string &b){
            return a.length() < b.length();
        });
        updateHelp(help,words);
        //print(help,words);
        int ans = 0;
        for(int i = 0;i < words.size();i++)
        {
            deal(help,i,1,ans);
        }
        return ans;
    }

private:
    void deal(vector<vector<int>> &help,int index, int cnt,int &ans)
    {
        if(help[index].empty())
        {
            if(ans < cnt)
                ans = cnt;
            return ;
        }
        for(auto indexNext : help[index])
        {
            deal(help,indexNext,cnt+1,ans);
        }
    }
    void print(vector<vector<int>> &help,vector<string>& words)
    {
        int i = 0;
        for(;i<help.size();i++)
        {
            cout<<"("<<words[i]<<") isSubOf=";
            for(int j = 0;j<help[i].size();j++)
            {
                cout<<words[help[i][j]]<<":";
            }
            cout<<endl;
        }
    }
    void updateHelp(vector<vector<int>> &help,vector<string>& words)
    {
        int i = 0;
        int len = words.size();
        //cout<<__LINE__<<":"<<help.size()<<":"<<words.size()<<endl;
        while(i < len)
        {
            int choice = i;
            int find_len = 0;
            int j = choice+1;
            bool run = true;
            while(j < len && run)
            {
                if(words[j].length() > words[i].length())
                {

                    if(find_len == 0)
                    {
                        if(isSubStr(words[i],words[j]))
                        {
                            help[choice].emplace_back(j);
                            find_len = words[j].length();
                        }
                    }else{
                        if(words[j].length() != find_len)
                            run = false;
                        else{
                            if(isSubStr(words[i],words[j]))
                            {
                                help[choice].emplace_back(j);
                            }
                        }
                    }

                }
                j++;
            }
            i++;
        }
    }
    bool isSubStr(string &sub,string &s2)
    {

        int i = 0;
        int j = 0;
        while(i < sub.length()&& j < s2.length())
        {
            if(sub[i] == s2[j])
            {
                i++;
                j++;
            }else{
                j++;
            }
        }
        auto ret =  i == (sub.length());
        //cout<<sub<<":"<<s2<<":"<<(ret?"true":"false")<<endl;
        return ret;
    }
};
```
