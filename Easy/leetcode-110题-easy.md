平衡二叉数，所有子树也要平衡
Runtime: 16 ms, faster than 55.41%
Memory Usage: 17.4 MB, less than 62.71% 
[https://leetcode.com/problems/balanced-binary-tree/](https://leetcode.com/problems/balanced-binary-tree/)
求出每个根节点的深度即可
```
class Solution {
public:
    bool isBalanced(TreeNode* root) {
        if(root)
            return abs(Depth(root->left) - Depth(root->right)) <= 1 && isBalanced(root->left) && isBalanced(root->right);
        return true;
    }
private:
    int Depth(TreeNode *root)
    {
        if(root)
            return 1 + max(Depth(root->left),Depth(root->right));
        return 0;
    }
};
```
