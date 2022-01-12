```python
class Solution:
    def maxProfit(self, prices: List[int], fee: int) -> int:
        profit = 0
        min_price = prices[0]
        
        for i in range(1, len(prices)):
            if prices[i] < min_price:
                min_price = prices[i]
            elif prices[i] > min_price and prices[i] - min_price - fee < 0:
                continue
            elif prices[i] - min_price - fee > 0:
                profit += prices[i] - min_price - fee
                min_price = prices[i] - fee
                
        return profit
```
