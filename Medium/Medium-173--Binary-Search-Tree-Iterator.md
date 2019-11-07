```
class BSTIterator {
public:
    BSTIterator(TreeNode* root) {
        i = 0;
        preSreach(preTree,root);
        sort(preTree.begin(),preTree.end());
    }

    /** @return the next smallest number */
    int next() {
        return preTree[i++];
    }

    /** @return whether we have a next smallest number */
    bool hasNext() {
        return i < preTree.size();
    }

private:
    int i = 0;
    vector<int> preTree;
    void preSreach(vector<int>& preTree,TreeNode *root)
    {
        if(root)
        {
            preSreach(preTree,root->left);
            preTree.emplace_back(root->val);
            preSreach(preTree,root->right);
        }
    }
};
```
