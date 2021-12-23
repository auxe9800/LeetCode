```python
class Solution:
    def combinationSum2(self, candidates: List[int], target: int) -> List[List[int]]:
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
                if i > start_index and candidates[i] == candidates[i-1]:
                    continue
                path.append(candidates[i])
                backtracking(candidates, target, i+1)
                path.pop()
                
        candidates.sort()
        backtracking(candidates, target, 0)
        return res
```
