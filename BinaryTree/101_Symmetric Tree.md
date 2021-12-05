```python
class Solution:
    def isSymmetric(self, root: Optional[TreeNode]) -> bool:
        if not root:
            return True
        
        stack = []
        stack.append(root.left)
        stack.append(root.right)
        
        while stack:
            left = stack.pop()
            right = stack.pop()
            
            if left is None and right is None:
                continue
            if left is None or right is None or left.val != right.val:
                return False
            
            stack.append(left.left)
            stack.append(right.right)
            stack.append(left.right)
            stack.append(right.left)
        
        return True
```
