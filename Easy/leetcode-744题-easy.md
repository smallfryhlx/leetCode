求一个字符列表中找一个大于某个字符的最小字符
Runtime: 16 ms, faster than 51.83% of C++ online submissions for Find Smallest Letter Greater Than Target.
Memory Usage: 9.1 MB, less than 54.55% of C++ online submissions for Find Smallest Letter Greater Than Target.
[https://leetcode.com/problems/find-smallest-letter-greater-than-target/](https://leetcode.com/problems/find-smallest-letter-greater-than-target/)
```
class Solution {
public:
    //要么找最小的   要么找大于他的最小的
    char nextGreatestLetter(vector<char>& letters, char target) {
        char min = letters[0];
        int len = letters.size();
        char min_beyond_tar = 0;
        for(int i = 0;i < len; i++)
        {
            if(min > letters[i])
            {
                min = letters[i];
            }
            if(letters[i] > target)
            {
                if(min_beyond_tar == 0)
                {
                    min_beyond_tar = letters[i];
                }else if(min_beyond_tar > letters[i]){
                    min_beyond_tar = letters[i];
                }
            }
        }
        return min_beyond_tar==0?min:min_beyond_tar;
    }
};
```
