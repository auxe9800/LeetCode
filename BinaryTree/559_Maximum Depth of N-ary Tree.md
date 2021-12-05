```python
class Solution:
    def maxDepth(self, root: 'Node') -> int:
        _max = 0
        
        if not root:
            return _max
        
        from collections import deque
        que = deque([root])
        
        while que:
            n = len(que)
            _max += 1
            
            for _ in range(n):
                cur = que.popleft()
                
                for j in range(len(cur.children)):
                    if cur.children[j]:
                        que.append(cur.children[j])
        return _max
```
