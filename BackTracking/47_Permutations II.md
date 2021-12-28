```python
class Solution:
    def permuteUnique(self, nums: List[int]) -> List[List[int]]:
        path = []
        paths = []
        used = [False] * len(nums)
        
        def backtracking(nums):
            nonlocal path
            nonlocal paths
            nonlocal used
            
            if len(nums) == len(path):
                paths.append(path.copy())
                return
            
            for i in range(0, len(nums)):
                if not used[i]:
                    if i > 0 and nums[i-1] == nums[i] and not used[i-1]:
                        continue
                    used[i] = True
                    path.append(nums[i])
                    backtracking(nums)
                    path.pop()
                    used[i] = False
                    
        backtracking(sorted(nums))
        return paths
```
