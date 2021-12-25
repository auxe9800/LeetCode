```python
class Solution:
    def partition(self, s: str) -> List[List[str]]:
        res = []
        path = []
        
        def backtracking(s, start_index):
            nonlocal res
            nonlocal path
            
            if start_index >= len(s):
                res.append(path[:])
                return
                
            for i in range(start_index, len(s)):
                temp = s[start_index:i+1]
                
                if temp == temp[::-1]:
                    path.append(temp)
                    backtracking(s, i+1)
                    path.pop()
                    
        backtracking(s, 0)
        return res
        
```
