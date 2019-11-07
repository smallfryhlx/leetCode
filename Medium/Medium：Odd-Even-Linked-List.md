链表奇数位节点放在偶数位节点前面
[https://leetcode.com/problems/odd-even-linked-list/](https://leetcode.com/problems/odd-even-linked-list/)
```
class Solution {
public:
    ListNode* oddEvenList(ListNode* head) {
        if(!head || !head->next)
            return head;
        auto odd = head;
        auto even = head->next;
        auto evenHead = even;
        int i = 1;
        auto node = even->next;
        while(node)
        {
            if(i%2 == 1)
            {
                odd->next = node;
                odd = odd->next;
            }else{
                even->next = node;
                even = even->next;
            }
            node = node->next;
            i++;
        }
        odd->next = evenHead;
        even->next = nullptr;
        auto no = head;
        cout<<head->val<<endl;
        int j = 0;
        while(no && j <8)
        {
            cout<<no->val<<endl;
            no = no->next;
            j++;
        }

        return head;
    }
};
```
