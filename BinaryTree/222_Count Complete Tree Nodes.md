```python
class Solution:
    def countNodes(self, root: Optional[TreeNode]) -> int:
        if not root:
            return 0
        
        total = 0
        from collections import deque
        que = deque([root])
        
        while que:
            n = len(que)
            for _ in range(n):
                cur = que.popleft()
                total += 1
                
                if cur.left:
                    que.append(cur.left)
                if cur.right:
                    que.append(cur.right)
        return total
```
