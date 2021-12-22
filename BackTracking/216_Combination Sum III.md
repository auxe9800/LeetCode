```python
class Solution:
    def combinationSum3(self, k: int, n: int) -> List[List[int]]:
        res = []
        path = []
        
        def backtracking(k, n, index):
            if sum(path) > n:
                return
            if len(path) == k:
                if sum(path) == n:
                    res.append(path[:])
                return
            
            for i in range(index, 9 - (k - len(path)) + 2):
                path.append(i)
                backtracking(k, n, i+1)
                path.pop()
        
        backtracking(k, n, 1)
        return res
```
