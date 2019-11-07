单向链表值是不是回文
Runtime: 24 ms, faster than 66.88%
Memory Usage: 12.5 MB, less than 84.48%
[https://leetcode.com/problems/palindrome-linked-list/](https://leetcode.com/problems/palindrome-linked-list/)
主要是借助一个new出来的的节点将后半段链表逆向连接
```
class Solution {
public:
    bool isPalindrome(ListNode* head) {
        int len = 0;
        auto node = head;
        auto *head2 = new ListNode(0);

        int index = 0;
        while(node)
        {
            node = node->next;
            len++;
        }
        int middle_node_index = (len+1)/2;
        node = head;
        while(node)
        {
            if(index == middle_node_index)
            {
                head2->next = node;
                break;
            }
            index++;
            node = node->next;
        }

        node = head2->next;

        while(node && node->next)
        {
            auto next_node = node->next;
            node->next = next_node->next;
            next_node->next = head2->next;
            head2->next = next_node;
        }
        auto node1 = head2->next;
        node = head;
        for(int i = 0;i < (len)/2 && node && node1; i++)
        {
            if(node->val != node1->val)
            {
                return false;
            }
            node = node->next;
            node1 = node1->next;
        }
        return true;
    }
};
```
