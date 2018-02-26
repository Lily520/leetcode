动态规划

分析：
我们利用两个变量，一个是最低买入价格，一个是当前的最大利润。遍历股票价格，如果当前股票价格低于目前最低买入价格，则更新最低买入价格；如果当前股票价格与最低买入价格之差大于目前最大利润，则更新最大利润。

```python
class Solution:
    def maxProfit(self, prices):
        """
        :type prices: List[int]
        :rtype: int
        """
        if len(prices) == 0:
            return 0

        buy_price = prices[0] #保存最低买入价格
        max_profit = 0 #当前最大利润

        for ele in prices[1:]:
            if ele < buy_price: #如果当前价格小于之前最低买入价格，更新最低买入价格buy_price
                buy_price = ele
            if ele - buy_price > max_profit:#如果当前价格与最低买入价格之差大于目前最大利润，更新最大利润max_profit
                max_profit = ele - buy_price

        return max_profit
                
```
