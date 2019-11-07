求一个树是不是另一个树的子树，对比要比较的树的每个节点
Runtime: 28 ms, faster than 74.47% 
Memory Usage: 20.7 MB, less than 100.00%
```
class Solution {
public:
    bool isSubtree(TreeNode* s, TreeNode* t) {
        if(!s && !t)
            return true;
        if(s && t)
        {
            return isSameTree(s,t) || isSubtree(s->left,t) || isSubtree(s->right,t);
        }
        return false;
    }

private:
    bool isSameTree(TreeNode *root,TreeNode *t)
    {
        if(root && t)
        {
            return root->val == t->val && isSameTree(root->left,t->left) && isSameTree(root->right,t->right);
        }
        if(!root && !t)
        {
            return true;
        }
        return false;
    }
};
```
