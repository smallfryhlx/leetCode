第K个最大的数，利用最小堆即可
[https://leetcode.com/problems/kth-largest-element-in-an-array/](https://leetcode.com/problems/kth-largest-element-in-an-array/)
```
class Solution {
public:
    int findKthLargest(vector<int>& nums, int k) {
        //找到第K个最大的数 利用最小堆即可
        vector<int> heap;
        for(auto &num : nums)
        {
            if(heap.size() == k)
            {
                if(num > heap[0])
                {
                    heap[0] = num;
                    down(heap);
                    //heap[0] 下沉
                }
            }else{
               heap.emplace_back(num);
               up(heap);
               //上浮
            }
        }
        return heap[0];
    }
private:
    void down(vector<int> &heap)
    {
        int father = 0;
        int left = 2 * father + 1;
        int right = 2 * father + 2;
        while(left < heap.size())
        {
            int min_index = left;
            if(right < heap.size() && heap[right] < heap[left])
                min_index = right;
            if(heap[father] < heap[min_index]){
                return;
            }else{
                swap(heap[father],heap[min_index]);
                father = min_index;
                left = 2 * father + 1;
                right = 2 * father + 2;
            }
        }
    }
    void up(vector<int> &heap)
    {
        int child = heap.size() - 1;
        int father = (child - 1)/2;
        while(father >=0 && child > 0)
        {
            if(heap[father] < heap[child]){
                return;
            }else{
                swap(heap[father],heap[child]);
                child = father;
                father = (child - 1)/2;
                cout<<father<<endl;
            }
        }
    }
};

```
