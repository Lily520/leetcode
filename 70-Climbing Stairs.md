这是一道动态规划的题。

分析：
设f(n)表示爬n阶楼梯的方法数，要想爬到第n阶楼梯有两种方法：一是从(n-1)阶楼梯前进1步；二是从(n-2)阶楼梯前进两步。因此可得：
f(n)=f(n-1)+f(n-2)

```python
class Solution:
    def climbStairs(self, n):
        """
        :type n: int
        :rtype: int
        """

        f = [1,2] #一阶楼梯的方法数为1，两阶楼梯的方法数为2

        for i in range(2,n):
            count = f[i-1]+f[i-2] #i个台阶时的方法数f(i)=f(i-1)+f(i-2)
            f.append(count)
        return f[n-1]
        

```
