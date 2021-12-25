```python
class Solution:
    def restoreIpAddresses(self, s: str) -> List[str]:
        res = []
        path = []
        
        def backtracking(s, start_index):
            nonlocal res
            nonlocal path
            
            if start_index == len(s) and len(path) == 4:
                res.append(".".join(path))
                return
                
            for i in range(start_index, len(s)):
                temp = s[start_index: i+1]
                if int(temp) >= 0 and int(temp) <= 255:
                    if len(temp) > 1 and temp[0] == "0":
                        continue
                    path.append(temp)
                    backtracking(s, i+1)
                    path.pop()
        
        backtracking(s, 0)
        return res
```
