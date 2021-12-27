```python
class Solution:
    def findSubsequences(self, nums: List[int]) -> List[List[int]]:
        res = []
        path = []
        
        def backtracking(nums, start_index):
            nonlocal res
            nonlocal path
            used = set()
            
            if len(path) >= 2:
                res.append(path[:])
                
            for i in range(start_index, len(nums)):
                if (path and path[-1] > nums[i]) or nums[i] in used:
                    continue
                used.add(nums[i])
                path.append(nums[i])
                backtracking(nums, i+1)
                path.pop()
                
        backtracking(nums, 0)
        return res
```
