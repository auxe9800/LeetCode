```python
class Solution:
    def subsetsWithDup(self, nums: List[int]) -> List[List[int]]:
        res = []
        path = []
        
        def backtracking(nums, start_index):
            nonlocal res
            nonlocal path
            
            res.append(path[:])
            
            for i in range(start_index, len(nums)):
                if i > start_index and nums[i] == nums[i-1]:
                    continue
                path.append(nums[i])
                backtracking(nums, i+1)
                path.pop()
                
        nums.sort()
        backtracking(nums, 0)
        return res
```
