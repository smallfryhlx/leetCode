求两个链表在哪里就是重合了
Runtime: 52 ms, faster than 54.51% 
Memory Usage: 16.7 MB, less than 90.74%
[https://leetcode.com/problems/intersection-of-two-linked-lists/](https://leetcode.com/problems/intersection-of-two-linked-lists/)

把两个链表化成一样的长度 开始找 o(n)
```
class Solution {
public:
    ListNode *getIntersectionNode(ListNode *headA, ListNode *headB) {
        int lenA = 0;
        int lenB = 0;
        ListNode *ptr = nullptr;
        ptr = headA;
        while(ptr)
        {
            ptr = ptr->next;
            lenA++;
        }
        ptr = headB;
        while(ptr)
        {
            ptr = ptr->next;
            lenB++;
        }
        ListNode *nodeA = headA;
        ListNode *nodeB = headB;
        if(lenA < lenB)
        {
            int i = 0;
            while(nodeB && i<(lenB - lenA))
            {
                nodeB = nodeB->next;
                i++;
            }
        }else if(lenA == lenB){

        }else{
            int i = 0;
            while(nodeA && i < (lenA - lenB))
            {
                nodeA = nodeA->next;
                i++;
            }
        }

        while(nodeA && nodeB)
        {
            if(nodeA == nodeB)
            {
                return nodeA;
            }else{
                nodeA = nodeA->next;
                nodeB = nodeB->next;
            }
        }
        return nullptr;
    }
};
```
