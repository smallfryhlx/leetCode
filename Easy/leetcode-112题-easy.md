找到二叉树的某一条路径的和等于一个值，有就返回true
Runtime: 12 ms, faster than 75.59%
Memory Usage: 19.7 MB, less than 100.00%
DFS搜索
```
class Solution {
public:
    bool hasPathSum(TreeNode* root, int sum) {
        if(!root)
            return false;
        if(root->right == nullptr && root->left == nullptr && sum == root->val)
        {
            return true;
        }
        bool left = hasPathSum(root->left,sum-root->val);
        bool right = hasPathSum(root->right,sum-root->val);
        return left || right;
    }

private:
};
```
