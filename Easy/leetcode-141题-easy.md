判断一个链表是否是循环链表
Runtime: 12 ms, faster than 72.60% 
Memory Usage: 9.8 MB, less than 75.00%
使用两个节点  一个每次走一步 一个每次走两步
如果是循环链表总会相遇的
```
class Solution {
public:
    bool hasCycle(ListNode *head) {
        if(!head)
            return false;
        auto next_one = head;
        auto next_two = head->next;
        if(!next_one)
            return true;
        while(next_one && next_two && next_two->next)
        {
            if(next_one == next_two)
                return true;
            next_one = next_one->next;
            next_two = next_two->next->next;
        }
        return false;
    }
};
```
