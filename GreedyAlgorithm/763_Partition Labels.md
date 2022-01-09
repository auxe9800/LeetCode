```python
class Solution:
    def partitionLabels(self, s: str) -> List[int]:
        result = []
        last = {}
        
        for i in range(len(s)):
            last[s[i]] = i
        
        right = 0
        left = 0
        for i in range(len(s)):
            right = max(last[s[i]], right)
            if right == i:
                result.append(right - left + 1)
                left = i + 1
                
        return result
```
