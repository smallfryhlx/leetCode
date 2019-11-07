配对括号 stack
Runtime: 0 ms, faster than 100.00%
Memory Usage: 8.5 MB, less than 73.64%
```

class Solution {
public:
    bool isValid(string s) {
        std::stack<char> stack1;
        int len = s.length();
        for(int i =0;i<len;i++)
        {
            if(stack1.empty())
            {
                stack1.emplace(s[i]);
            }else{
                auto left = stack1.top();
                if(isRight(left))
                {
                    return false;
                }
                if(isPair(left,s[i]))
                {
                    stack1.pop();
                }else{
                    if(isRight(s[i])){
                        return false;
                    }
                    stack1.emplace(s[i]);
                }
            }
        }
        return stack1.empty();
    }
private:
    bool isRight(char &ch)
    {
        return ch==')' || ch == ']' || ch == '}';
    }
    bool isPair(char &left,char &right )
    {
        if(left == '(' && right == ')')
            return true;
        if(left == '{' && right == '}')
            return true;
        return left == '[' && right == ']';
    }
};

```
