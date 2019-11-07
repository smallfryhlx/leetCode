广度优先搜索
[https://leetcode.com/problems/binary-tree-level-order-traversal/](https://leetcode.com/problems/binary-tree-level-order-traversal/)

```
class Solution {
public:
    vector<vector<int>> levelOrder(TreeNode* root) {
        //广度优先遍历
        vector<vector<int>> ans;
        if(!root)
            return ans;
        queue<TreeNode *> help;
        help.emplace(root);
        while(!help.empty())
        {
            int size = help.size();
            int i = 0;
            vector<int> data;
            while(i < size)
            {
                auto node = help.front();
                help.pop();
                data.emplace_back(node->val);
                if(node->left)
                    help.emplace(node->left);
                if(node->right)
                    help.emplace(node->right);
                i++;
            }
            ans.emplace_back(move(data));
        }
        return ans;
    }
};
```
