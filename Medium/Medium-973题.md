K Closest Points to Origin
找离原点最近的K个点，就是最大堆的应用
[https://leetcode.com/problems/queue-reconstruction-by-height/](https://leetcode.com/problems/queue-reconstruction-by-height/)
```
class Solution {
public:
    vector<vector<int>> kClosest(vector<vector<int>>& points, int K) {
        vector<vector<int>> ans;
        vector<Info> heap;//最大堆
        for(auto &point : points)
        {
            Info info;
            info.point = make_pair(point[0],point[1]);
            info.dis = point[0] * point[0] + point[1] * point[1];

            if(heap.size() == K)
            {
                if(info.dis < heap[0].dis)
                {
                    heap[0] = info;
                    down(heap);
                }
            }else{
                heap.emplace_back(info);
                up(heap);
            }
        }
        cout<<heap.size()<<endl;
        for(auto &info : heap)
        {
            //cout<<info.point.first<<"::"<<info.point.second<<endl;
            vector<int> tmp{info.point.first,info.point.second};
            ans.emplace_back(tmp);
        }
        return ans;
    }
private:
    struct Info{
        pair<int,int> point;
        int dis = 0;
    };
    void down(vector<Info> &heap)
    {
        int father = 0;
        int left = 2 * father + 1;
        int right = 2 * father + 2;
        while(left < heap.size())
        {
            int max_index = left;
            if(right < heap.size() && heap[left].dis < heap[right].dis)
            {
                max_index = right;
            }
            if(heap[max_index].dis > heap[father].dis){
                swap(heap[max_index],heap[father]);
                father = max_index;
                left = 2 * father + 1;
                right = 2 * father + 2;
            }else{
                return;
            }
        }
    }
    void up(vector<Info> &heap)
    {
        int father = (heap.size()-1 - 1)/2;
        int child = heap.size()-1;
        while(father >= 0)
        {
            if(heap[father].dis < heap[child].dis)
            {
                swap(heap[father],heap[child]);
                child = father;
                father = (child - 1)/2;
            }else
                return;
        }
    }
};
```
