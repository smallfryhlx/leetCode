[https://leetcode.com/problems/find-largest-value-in-each-tree-row/](https://leetcode.com/problems/find-largest-value-in-each-tree-row/)

//广度优先搜索
```
class Solution {
public:
    vector<int> largestValues(TreeNode* root) {
        queue<TreeNode *> q;
        vector<int> ans;
        if(!root)
            return ans;
        q.emplace(root);
        while (!q.empty())
        {
            int max = q.front()->val;
            int len = q.size();
            int i = 0;
            while(i < len)
            {
                auto node = q.front();
                if(max < node->val)
                    max = node->val;
                if(node->left)
                    q.emplace(node->left);
                if(node->right)
                    q.emplace(node->right);
                q.pop();
                i++;
            }
            ans.emplace_back(max);
        }
        return ans;
    }
};
```
