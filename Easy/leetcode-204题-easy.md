找出小于n的所有素数的个数，n为正数。
Runtime: 28 ms, faster than 83.56% 
Memory Usage: 8.4 MB, less than 91.67%
(主要就是利用数组；然后利用小的数，更新是他倍数的大数不是素数)
####代码实现
```
class Solution {
public:
    int countPrimes(int n) {
       if(n<=2)
           return 0;
       int8_t isNotPrime[n/8+1]={0};
       for(int i = 2;i*i<n;i++)
       {
           if(getisNotPrime(isNotPrime,i))
               continue;
           for(int j = i*i;j<n;j+=i)
                setisNotPrime(isNotPrime,j);
       }
       int cnt =0;
       for(int i = 2;i<n;i++)
       {
           cnt += getisNotPrime(isNotPrime,i)?0:1;
       }
       return cnt;
    }
private:
    int getisNotPrime(int8_t arr[],int index)
    {
        int a = index / 8;
        int b = index % 8;
        return (arr[a] >> b) & 1;
    }
    void  setisNotPrime(int8_t arr[], int index)
    {
        int a = index / 8;
        int b = index % 8;
        arr[a] |= 1<<b;
    }
};
```
