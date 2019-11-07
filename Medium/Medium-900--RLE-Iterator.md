奇数位为偶数位出现的次数  利用链表即可
```
class RLEIterator {
private:
    struct Node{
        Node(int time,int v)
        {
            times = time;
            val = v;
            next = nullptr;
        }
      int times = 0;
      int val = 0 ;
      Node *next = nullptr;
    };
public:
    explicit RLEIterator(vector<int>& A) {
        //i i+1
       Node *former = nullptr;
       for(int i = 0; (i+1) < A.size();i+=2)
       {
           if(A[i] == 0)
               continue;
           auto newNode = new Node(A[i],A[i+1]);
           if(former == nullptr)
           {
               head = newNode;
           }else{
                former->next = newNode;
           }
           former = newNode;
       }
    }

    int next(int n) {
        while(n > 0)
        {
            if(head == nullptr)
                return -1;
            auto first = head;
            if(first->times > n)
            {
                first->times -= n;
                return first->val;
            }else if(first->times == n){
                auto del = head;
                head = head->next;
                auto ret = del->val;
                delete(del);
                return ret;
            }else{
                n -= first->times;
                auto del = head;
                head = head->next;
                delete(del);
            }
        }
        return -1;
    }
private:
    Node *head;
};
```
