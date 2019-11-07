[https://leetcode.com/problems/add-two-numbers-ii/](https://leetcode.com/problems/add-two-numbers-ii/)
两个链表当成两个数字  相加 返回一个链表 表示他们的和
递归思想
Runtime: 20 ms, faster than 92.01% of C++ online submissions for Add Two Numbers II.
Memory Usage: 9.7 MB, less than 100.00% of C++ online submissions for Add Two Numbers II.
```
class Solution {
public:
    ListNode* addTwoNumbers(ListNode* l1, ListNode* l2) {
            auto len1 = getLen(l1);
            auto len2 = getLen(l2);
            auto bigger = l1;
            auto smaller = l2;
            if(len1 < len2)
            {
                bigger = l2;
                smaller = l1;
            }
            int diff = abs(len1-len2);
            auto node1 = bigger;
            for(int i = 0; i < diff;i++)
                node1 = node1->next;
            auto node2 = smaller;
            while(node1 && node2)
            {
                node1->val = node1->val + node2->val;
                node1 = node1->next;
                node2 = node2->next;
            }
        //Print(bigger);
            update(bigger);

            if(bigger->val >= 10)
            {
                bigger->val -= 10;
                auto hea = new ListNode(1);
                hea->next = bigger;
                bigger  = hea;
            }
            return bigger;
    }

public:
    void update(ListNode *node)
    {
        if(node)
        {
            update(node->next);
            auto next = node->next;
            if(next)
            {
                if(next->val >= 10)
                {
                    node->val += 1;
                    next->val -= 10;
                }
            }

        }
    }
    void Print(ListNode *head)
    {
        auto node = head;
        while(node)
        {
            cout<<node->val<<endl;
            node = node->next;
        }
    }
    int getLen(ListNode *head)
    {
        auto node = head;
        int len = 0;
        while(node)
        {
            len++;
            node = node->next;
        }
        return  len;
    }
};
```
