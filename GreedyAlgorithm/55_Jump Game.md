```python
class Solution:
    def canJump(self, nums: List[int]) -> bool:
        cover = 0
        i = 0
        
        while i <= cover:
            cover = max(cover, i+nums[i])
            if cover >= (len(nums) - 1):
                return True
            i += 1
            
        return False
```
