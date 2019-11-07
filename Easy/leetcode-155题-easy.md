实现一个可以得到随时得到最小值的数组
Runtime: 32 ms, faster than 67.65%
Memory Usage: 16.8 MB, less than 100.00% 
[https://leetcode.com/problems/min-stack/](https://leetcode.com/problems/min-stack/)
```
class MinStack {
public:
    /** initialize your data structure here. */
    MinStack() = default;

    void push(int x) {
        if(len == 0)
        {
            min = x;
        }else if(x < min)
        {
            min = x;
        }
        vec.emplace_back(x);
        len++;
    }

    void pop() {
        if(len == 0)
        {
            return;
        }else if(vec[len-1] == min)
        {
            getMinNum();
        }
        len--;
        vec.pop_back();
    }

    int top() {
        return *vec.rbegin();
    }
    int getMin() {
        return min;
    }

private:
    void getMinNum()
    {
        int i = 0;
        min = vec[0];
        for(;i<len-1;i++)
        {
            if(vec[i] < min)
                min = vec[i];
        }
    }
    int len = 0;
    int min = 0;
    std::vector<int> vec={};
};
```
