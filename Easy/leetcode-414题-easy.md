找到第三个最大的数，相同的数算一个，不足三个最大数，返回最大数
Runtime: 8 ms, faster than 78.22%
Memory Usage: 9.1 MB, less than 76.92%
- [https://leetcode.com/problems/third-maximum-number/submissions/](https://leetcode.com/problems/third-maximum-number/submissions/)
####实现代码
```
//用堆的话也要每次找有没有一样的值，因为只要三个所以就用数组好了。
class Solution {
public:
    int thirdMax(vector<int>& nums)
    {
        for(auto &num : nums)
        {
            insert(num);
        }
        if(size < 3){
            return arr[2];
        }
        return arr[0];
    }
private:
    void insert(int &x)
    {
        if(size == 0)
        {
            arr[2] = x;
            size++;
        }else if(size == 1){
            if(x == arr[2])
            {
                return;
            }else{
                if(x > arr[2])
                {
                    arr[0] = arr[2];
                    arr[2] = x;
                }else{
                    arr[0] = x;
                }
                size++;
            }
        }else if(size == 2){
            if(x == arr[0] || x == arr[2])
            {
                return;
            }else{
                if(x < arr[0]){
                    arr[1] = arr[0];
                    arr[0] = x;
                }else if(x > arr[2]){
                    arr[1] = arr[2];
                    arr[2] = x;
                }else{
                    arr[1] = x;
                }
                size++;
            }
        }else{//size ==3;
            if(x == arr[0] || x == arr[1] || x == arr[2])
            {
                return;
            }else if( x < arr[0]){
                return;
            }else if(arr[0] < x && x < arr[1]){
                arr[0] = x;
            } else if(arr[1] < x && x < arr[2]){
                arr[0] = arr[1];
                arr[1] = x;
            } else if(arr[2] < x){
                arr[0] = arr[1];
                arr[1] = arr[2];
                arr[2] = x;
            }
        }
    }
    int arr[3] = {0,0,0};
    int size = 0;
};
```
