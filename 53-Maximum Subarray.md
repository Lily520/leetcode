最大连续子序列和，这是动态规划的一道简单题。

分析：

遍历序列时，对于序列中的一个数，只有两种选择： 

1.如果之前Subarray的和大于0的话，我们认为它对后续结果是有益的。此时，我们将这个数加入之前的Subarray； 

2.如果之前Subarray的和小于等于0的话，我们认为他对后续结果有害。此时，我们将以这个数字开始，组成新的Subarray。 


代码：

```python
class Solution:
    def maxSubArray(self, nums):
        """
        :type nums: List[int]
        :rtype: int
        """
        
        preSum = 0
        maxSum = nums[0]
        
        for ele in nums:
            preSum = max(preSum+ele,ele)
            maxSum = max(preSum,maxSum)
            
        return maxSum  
```
