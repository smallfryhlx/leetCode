最大堆求最小k个数
[https://leetcode.com/problems/kth-smallest-element-in-a-bst/](https://leetcode.com/problems/kth-smallest-element-in-a-bst/)

```
class Solution {
public:
    int kthSmallest(TreeNode* root, int k)
    {
        vector<int > heap;
        EleSearch(root,heap,k);
        return heap[0];
    }

private:
    void EleSearch(TreeNode *root,vector<int > &heap,int k)
    {
        if(root)
        {
            EleSearch(root->left,heap,k);
            EleSearch(root->right,heap,k);
            InsertToHeap(heap,k,root->val);
        }
    }
    //最大堆  父亲永远大于两个儿子
    void InsertToHeap(vector<int > &heap,int k,int ele)
    {
        if(heap.size() == k)
        {
            if(heap[0] > ele)
            {
                heap[0] = ele;
                //down
                down(heap);
            }
        }else{
            heap.emplace_back(ele);
            //up
            up(heap);
        }
    }
    void up(vector<int > &heap)
    {
        int son = heap.size() - 1;
        int parent = (son - 1)/2;
        while(parent >=0 && heap[parent] < heap[son])
        {
            swap(heap[parent] , heap[son]);
            son = parent;
            parent = (son - 1)/2;
        }
    }
    void down(vector<int > &heap)
    {
        int parent = 0;
        int left = 2 * parent + 1;
        int right = 2 * parent + 2;
        while(left < heap.size())
        {
            int max_index = left;
            if(right < heap.size() && heap[right] > heap[max_index])
                max_index = right;
            if(heap[max_index] > heap[parent]){
                swap(heap[max_index] , heap[parent]);
                parent = max_index;
                left = 2 * parent + 1;
                right = 2 * parent + 2;
            } else{
                return;
            }
        }
    }
};
```
