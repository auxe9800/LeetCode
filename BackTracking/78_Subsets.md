```python
class Solution:
    def subsets(self, nums: List[int]) -> List[List[int]]:
        res = []
        path = []
        
        def backtracking(nums, start_index):
            nonlocal res
            nonlocal path
            
            res.append(path[:])
            if start_index >= len(nums):
                return
                
            for i in range(start_index, len(nums)):
                path.append(nums[i])
                backtracking(nums, i+1)
                path.pop()
                
        backtracking(nums, 0)
        return res
```
