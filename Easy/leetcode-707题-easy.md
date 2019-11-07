说明：实现一个链表，可以往头部，尾部，index位置添加数据，可以删除index位置节点数据。
-  [https://leetcode.com/problems/design-linked-list/submissions/](https://leetcode.com/problems/design-linked-list/submissions/)
***难度：easy***
Runtime: 48 ms, faster than 62.47%
Memory Usage: 19.3 MB, less than 77.78%
####代码实现
```
class MyLinkedList {
private:
    struct Node{
        int val = 0;
        Node *next= nullptr;
    };
    int size = 0;
    Node *head = nullptr;
    Node *tail = nullptr;
public:
    MyLinkedList() {
    }
    int get(int index) {
        Node *node = head;
        if(index >=0 && index < size)
        {
            int i = 0;
            while(node && i < index)
            {
                node = node->next;
                i++;
            }
            if(i == index)
                return node->val;
        }
        return -1;
    }
    void addAtHead(int val) {
        auto addHead = new Node();
        addHead->val = val;
        addHead->next = head;
        if(size == 0)
        {
            head = tail = addHead;
            size++;
            return;
        }
        head = addHead;
        size++;
    }
    void addAtTail(int val) {
        auto addtail = new Node();
        addtail->next = nullptr;
        addtail->val = val;
        if(size == 0)
        {
            head = tail = addtail;
            size++;
            return ;
        }
        tail->next = addtail;
        tail = addtail;
        size++;
    }
    void addAtIndex(int index, int val) {
        if(index > size)
            return;
        if(index == size)
        {
            addAtTail(val);
        }else if(index <= 0){
            addAtHead(val);
        }else{
            auto nodeAtindexBefore = getNodeAtIndexBefore(index);
            auto addNode = new Node();
            addNode->val = val;
            addNode->next = nodeAtindexBefore->next;
            nodeAtindexBefore->next = addNode;
            size++;
        }
    }
    void deleteAtIndex(int index) {
        if(index <0 || index >= size)
            return;
        if(index == 0 && head)
        {
            auto del = head;
            head = head->next;
            size--;
            delete(del);
            return;
        }
        auto nodeAtIndexBefore = getNodeAtIndexBefore(index);
        if(index == size - 1)
        {
            tail = nodeAtIndexBefore;
        }
        auto del = nodeAtIndexBefore->next;
        nodeAtIndexBefore->next = nodeAtIndexBefore->next->next;
        delete(del);
        size--;
    }
private:
    Node *getNodeAtIndexBefore(int index)
    {
        int find = index-1;
        auto findNode = head;
        if(0<=find && find<=size-1)
        {
            int i = 0;
            while(findNode && i < find)
            {
                findNode = findNode->next;
                i++;
            }
            if(i == find)
                return findNode;
        }
        return nullptr;
    }
};
```
