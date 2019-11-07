删除节点 使得有序链表中相同的数值只存在一个
Runtime: 8 ms, faster than 97.63% 
Memory Usage: 9.2 MB, less than 98.11% 
[https://leetcode.com/problems/remove-duplicates-from-sorted-list/](https://leetcode.com/problems/remove-duplicates-from-sorted-list/)
```
class Solution {
public:
    ListNode* deleteDuplicates(ListNode* head) {
        auto node = head;
        if(head)
        {
            auto cmp_node = node->next;
            while (node && cmp_node)
            {
                if(node->val == cmp_node->val)
                {
                    node->next = cmp_node->next;
                    cmp_node = node->next;
                }else{
                    node = node->next;
                    cmp_node = node->next;
                }
            }
        }
        return head;
    }
};
```
