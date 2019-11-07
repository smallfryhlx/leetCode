树是不是一个对称的树
Runtime: 8 ms, faster than 47.02%
Memory Usage: 14.8 MB, less than 79.66%
root的子树对称的地方一直相等即可
```
class Solution {
public:
    bool isSymmetric(TreeNode* root) {
        if(!root)
            return true;
        return isSymm(root->left,root->right);
    }

private:
    bool isSymm(TreeNode *left,TreeNode *right)
    {
        if(left && right)
            return left->val == right->val && isSymm(left->right,right->left) && isSymm(left->left,right->right);
        return !left && !right;
    }

};
```
