//找出数组中每个数第一个大于此数的数
利用stack找出前面的数 所有小于 当前数 插入vector
```
class Solution {
public:
    vector<int> nextLargerNodes(ListNode* head) {
        vector<int> ans;
        int index = 0;
        stack<pair<int,int>> help;

        auto node = head;
        while(node)
        {
            ans.emplace_back(0);
            while(!help.empty() && help.top().second <  node->val)
            {
                ans[help.top().first] =  node->val;
                help.pop();
            }
            help.emplace(index,node->val);
            index++;
            node = node->next;
        }
        return ans;
    }
};
```
