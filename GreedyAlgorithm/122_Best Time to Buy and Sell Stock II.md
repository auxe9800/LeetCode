```python
class Solution:
    def maxProfit(self, prices: List[int]) -> int:
        profit = 0
        count = -1
        i = 0
        
        while i < len(prices):
            if count == -1:
                count = prices[i]
            else:
                sold = prices[i] - count
                if sold > 0:
                    profit += sold
                count = prices[i]
            i += 1
        return profit
```
