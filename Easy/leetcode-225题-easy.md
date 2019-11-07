利用queue写一个stack
Runtime: 4 ms, faster than 53.62% 
Memory Usage: 8.9 MB, less than 66.67%
[https://leetcode.com/problems/implement-stack-using-queues/](https://leetcode.com/problems/implement-stack-using-queues/)
```
class MyStack {
public:
    MyStack() = default;

    void push(int x) {
        helper.push(x);
        while(!stack.empty())
        {
            helper.push(stack.front());
            stack.pop();
        }
        while(!helper.empty())
        {
            stack.push(helper.front());
            helper.pop();
        }
    }

    int pop() {
        auto ret = stack.front();
        stack.pop();
        return ret;
    }

    int top() {
        return stack.front();
    }

    bool empty() {
        return stack.empty();
    }
//队列先进先出
private:
    std::queue<int> stack;
    std::queue<int> helper;
};
```
