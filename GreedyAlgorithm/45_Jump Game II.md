```python
class Solution:
    def jump(self, nums: List[int]) -> int:
        if len(nums) == 1:
            return 0
        cur_dist = 0
        next_dist = 0
        jumps = 0
        
        for i in range(len(nums)):
            next_dist = max(next_dist, i+nums[i])
            if i == cur_dist:
                if cur_dist != len(nums) - 1:
                    jumps += 1
                    cur_dist = next_dist
                    
                    if next_dist >= len(nums) - 1:
                        break
                else:
                    break
        return jumps
```
