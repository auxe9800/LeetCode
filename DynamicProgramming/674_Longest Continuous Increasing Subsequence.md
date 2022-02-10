```python
class Solution:
    def findLengthOfLCIS(self, nums: List[int]) -> int:
        dp = [1] * len(nums)
        result = 1
        
        for i in range(1, len(nums)):
            if nums[i] > nums[i-1]:
                dp[i] = dp[i-1]+1
            if dp[i] > result:
                result = dp[i]
                
        return result
```
