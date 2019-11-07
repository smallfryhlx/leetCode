因为是循环比较  所以吧一个数组copy一下 相当于处理2N 长度
时间复杂度 O(N)
```
class Solution {
public:
    vector<int> nextGreaterElements(vector<int>& nums) {
        vector<int> ans;
        stack<int> help;
        vector<int> ans_help;
        int len = nums.size();
        for(int i = 2 * len - 1;i>=0;i--)
        {
            int index = i % len;
            if(help.empty())
            {
                help.emplace(nums[index]);
                ans_help.emplace_back(-1);
            }else{
                auto front = help.top();
                if(front > nums[index])
                {
                    ans_help.emplace_back(front);
                    help.emplace(nums[index]);
                }else{
                    while(!help.empty() && help.top() <= nums[index])
                        help.pop();
                    ans_help.emplace_back(help.empty()?-1:help.top());
                    help.emplace(nums[index]);
                }
            }
        }
        for(int i = 2*len-1; i >=len;i--)
        {
            ans.emplace_back(ans_help[i]);
        }
//        for(auto num : ans)
//            cout<<__LINE__<<":"<<num<<endl;
        return ans;
    }
};
```
