```python
class Solution:
    def permute(self, nums: List[int]) -> List[List[int]]:
        path = []
        paths = []
        used = [False] * len(nums)
        
        def backtracking(nums):
            nonlocal path
            nonlocal paths
            
            if len(path) == len(nums):
                paths.append(path.copy())
                return
                
            for i in range(0, len(nums)):
                if used[i]:
                    continue
                used[i] = True
                path.append(nums[i])
                backtracking(nums)
                path.pop()
                used[i] = False
                
        backtracking(nums)
        return paths
```
