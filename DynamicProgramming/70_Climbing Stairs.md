```python
class Solution:
    def climbStairs(self, n: int) -> int:
        if n < 3:
            return n
        dp = [0] * 2
        dp[0] = 1
        dp[1] = 2
        
        for i in range(2, n):
            temp = dp[0] + dp[1]
            dp[0] = dp[1]
            dp[1] = temp
            
        return dp[1]
```
