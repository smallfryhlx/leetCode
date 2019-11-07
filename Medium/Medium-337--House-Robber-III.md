[https://leetcode.com/problems/house-robber-iii/](https://leetcode.com/problems/house-robber-iii/)
抢劫第三种类型，这次是抢树形房屋，相邻房屋不能抢
递归来做 ，也可以dp算法
ret = max(当前值+左左子树+左右子树+右右子树+右左子树 , 左子树+右子树)
```
class Solution {
public:
    int rob(TreeNode* root) {
        if(!root)
            return 0;
        int l = rob(root->left);
        int r = rob(root->right);
        int ll = 0;
        int lr = 0;
        int rl = 0;
        int rr = 0;
        if(root->left)
        {
            if(root->left->left)
            {
                ll = rob(root->left->left);
            }
            if(root->left->right)
            {
                lr = rob(root->left->right);
            }
        }
        if(root->right){
            if(root->right->left)
            {
                rl = rob(root->right->left);
            }
            if(root->right->right)
            {
                rr = rob(root->right->right);
            }
        }
        return max(root->val+ll+lr+rl+rr,l+r);
    }
};
```
