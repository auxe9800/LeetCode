```python
class Solution:
    def combinationSum(self, candidates: List[int], target: int) -> List[List[int]]:
        res = []
        path = []
        
        def backtracking(candidates, target, start_index):
            nonlocal res
            nonlocal path
            
            if sum(path) > target:
                return
            if sum(path) == target:
                res.append(path[:])
                return
            
            for i in range(start_index, len(candidates)):
                path.append(candidates[i])
                backtracking(candidates, target, i)
                path.pop()
                
        backtracking(candidates, target, 0)
        return res
```
