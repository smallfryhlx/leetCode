把链表上数值为val的节点都删除，new一个辅助节点即可
Runtime: 28 ms, faster than 65.16% 
Memory Usage: 10.8 MB, less than 100.00%
[https://leetcode.com/problems/remove-linked-list-elements/](https://leetcode.com/problems/remove-linked-list-elements/)
```
class Solution {
public:
    ListNode* removeElements(ListNode* head, int val) {
        auto myhead = new ListNode(0);
        myhead->next = head;
        auto node = myhead;
        while(node)
        {
            if(node->next && node->next->val == val)
            {
                node->next = node->next->next;
            }else{
                node = node->next;
            }
        }
        return myhead->next;
    }
};
```
