```python
class Solution:
    def integerBreak(self, n: int) -> int:
        dp = [1] * (n+1)
        
        for i in range(3, n+1):
            for j in range(1, i-1):
                dp[i] = max(dp[i], max(j*(i-j), j*dp[i-j]))
        return dp[-1]
```
