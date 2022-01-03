```python
class Solution:
    def maxSubArray(self, nums: List[int]) -> int:
        result = float("-inf")
        count = 0
        i = 0
        
        while i < len(nums):
            count += nums[i]
            if count > result:
                result = count
            if count <= 0:
                count = 0
            i += 1
            
        return result
```
