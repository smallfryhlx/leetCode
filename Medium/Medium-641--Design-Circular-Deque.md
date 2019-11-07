[https://leetcode.com/problems/design-circular-deque/](https://leetcode.com/problems/design-circular-deque/)
实现双端队列：利用双向链表实现
```
class MyCircularDeque {
private:
    struct DoubleListNode{
        explicit DoubleListNode(int val):val(val){}
        DoubleListNode *before = nullptr;
        DoubleListNode *next = nullptr;
        int val;
    };
    int len = 0;
    int k = 0;
    DoubleListNode *listHead = nullptr;
    DoubleListNode *tail = nullptr;
public:
    /** Initialize your data structure here. Set the size of the deque to be k. */
    MyCircularDeque(int k1) {
        k = k1;
        listHead = new DoubleListNode(-1);
        tail = nullptr;
        len = 0;
    }

    /** Adds an item at the front of Deque. Return true if the operation is successful. */
    bool insertFront(int value) {
        if(len == k)
            return false;
        auto node = new DoubleListNode(value);
        if(tail == nullptr){
            tail = node;
            tail->before = listHead;
            listHead->next = tail;
        }else{
            node->next = listHead->next;
            listHead->next->before = node;
            node->before = listHead;
            listHead->next = node;
        }
        len++;
        return true;
    }

    /** Adds an item at the rear of Deque. Return true if the operation is successful. */
    bool insertLast(int value) {
        if(len == k)
            return false;
        auto node = new DoubleListNode(value);
        if(tail == nullptr)
        {
            tail = node;
            tail->before = listHead;
            listHead->next = tail;
        }else{
            tail->next = node;
            node->before = tail;
            tail = node;
        }
        len++;
        return true;
    }

    /** Deletes an item from the front of Deque. Return true if the operation is successful. */
    bool deleteFront() {
        if(len == 0)
            return false;
        auto del = listHead->next;
        if(len == 1){
            delete(del);
            tail = nullptr;
            listHead->next = nullptr;
        }else{
            listHead->next = del->next;
            del->next->before = listHead;
            delete(del);
        }
        len--;
        return true;
    }

    /** Deletes an item from the rear of Deque. Return true if the operation is successful. */
    bool deleteLast() {
        if(len == 0)
            return false;
        auto del = tail;
        if(len == 1)
        {
            tail = nullptr;
            delete(del);
        }else{
            tail = del->before;
            tail->next = nullptr;
            delete(del);
        }
        len--;
        return true;
    }

    /** Get the front item from the deque. */
    int getFront() {
        return len==0?-1:listHead->next->val;
    }

    /** Get the last item from the deque. */
    int getRear() {
        return tail?tail->val:-1;
    }

    /** Checks whether the circular deque is empty or not. */
    bool isEmpty() {
        return len == 0;
    }

    /** Checks whether the circular deque is full or not. */
    bool isFull() {
        return len == k;
    }
};
```
