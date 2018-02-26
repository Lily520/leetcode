动态规划

分析：
设状态f(i)表示[0,i]的最大利润，g(i)表示[i,n-1]的最大利润，则最终的最大利润为max{f(i)+g(i)}。

```python
class Solution:
    def maxProfit(self, prices):
        """
        :type prices: List[int]
        :rtype: int
        """

        lens = len(prices)
        if lens == 0:
            return 0

        first = [0] * lens #[0,i]的最大利润
        min_buy = prices[0] #最低买入价格
        for i in range(lens):
            min_buy = min(min_buy,prices[i])
            first[i] = max(first[i-1],prices[i]-min_buy)

        second = [0] * lens #[i,n-1]的最大利润
        max_sell = prices[lens-1] #最大卖出价格
        for j in range(lens-2,-1,-1):
            max_sell = max(max_sell,prices[j])
            second[j] = max(second[j+1],max_sell-prices[j])

        max_profit = 0
        for m in range(lens):
            max_profit = max(max_profit,first[m]+second[m])
        return max_profit

```
