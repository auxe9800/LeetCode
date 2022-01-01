```python
class Solution:
    def wiggleMaxLength(self, nums: List[int]) -> int:
        if len(nums) <= 1:
            return len(nums)
        
        pre_diff = 0
        cur_diff = 0
        result = 1
        
        for i in range(1, len(nums)):
            cur_diff = nums[i] - nums[i - 1]
            if (cur_diff > 0 and pre_diff <= 0) or (cur_diff < 0 and pre_diff >= 0):
                result += 1
                pre_diff = cur_diff
                
        return result
```
