```python
class Solution:
    def findTargetSumWays(self, nums: List[int], target: int) -> int:
        sum_value = sum(nums)
        if abs(target) > abs(sum_value) or (target+sum_value) % 2 == 1:
            return 0
        
        bag_size = (sum_value + target) // 2
        dp = [0] * (bag_size+1)
        dp[0] = 1
        
        for i in range(len(nums)):
            for j in range(bag_size, nums[i]-1, -1):
                dp[j] += dp[j-nums[i]]
        return dp[bag_size]
```
