[https://leetcode.com/problems/validate-stack-sequences/](https://leetcode.com/problems/validate-stack-sequences/)
//是不是一个栈操作，利用一个栈模拟操作一下
```
class Solution {
public:
    bool validateStackSequences(vector<int>& pushed, vector<int>& popped) {
        int push = 0;
        int pop = 0;
        stack<int> help;
        while(push < pushed.size())
        {
            if(!help.empty() && help.top() == popped[pop])
            {
                //cout<<"pop:"<<help.top()<<endl;
                help.pop();
                pop++;
                while (!help.empty() && help.top() == popped[pop])
                {
                    help.pop();
                    pop++;
                }
            }
            //cout<<"push:"<<pushed[push]<<endl;
            help.emplace(pushed[push++]);
        }
        while(!help.empty())
        {
            if(help.top() == popped[pop])
            {
                help.pop();
                pop++;
            }else
                return false;
        }
        return help.empty();
    }
};
```
