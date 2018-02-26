贪心法

分析：
低进高出，把所有价格差为正的加起来就是最大利润。

```python
class Solution:
    def maxProfit(self, prices):
        """
        :type prices: List[int]
        :rtype: int
        """

        max_profit = 0

        for i in range(1,len(prices)):
            if prices[i] > prices[i-1]:#低进高出
                max_profit += prices[i] - prices[i-1]

        return max_profit
```
