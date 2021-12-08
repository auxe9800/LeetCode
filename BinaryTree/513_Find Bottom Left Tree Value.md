```python
class Solution:
    def findBottomLeftValue(self, root: Optional[TreeNode]) -> int:
        from collections import deque
        que = deque([root])
        
        res = []
        while que:
            n = len(que)
            res.clear()
            for _ in range(n):
                cur = que.popleft()
                if not cur.left and not cur.right:
                    res.append(cur.val)
                if cur.left:
                    que.append(cur.left)
                if cur.right:
                    que.append(cur.right)
            
        return res[0]
```
