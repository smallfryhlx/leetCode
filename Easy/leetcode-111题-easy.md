求二叉树的最小深度 
Runtime: 12 ms, faster than 75.66%
Memory Usage: 19.5 MB, less than 100.00%
[https://leetcode.com/problems/minimum-depth-of-binary-tree/](https://leetcode.com/problems/minimum-depth-of-binary-tree/)
求二叉树的最小深度 DFS注意 null节点深度不应该算成0
```
class Solution {
public:
    int minDepth(TreeNode* root) {
        int depth = 0;
        if(root)
        {
            depth += 1;
            if(root->left && root->right)
            {
                int left =  minDepth(root->left);
                int right = minDepth(root->right);
                depth += left < right? left : right;
            }
            else if(!root->right && root->left)
                depth += minDepth(root->left);
            else if(!root->left && root->right)
                depth += minDepth(root->right);
        }
        return depth;
    }
};
```
