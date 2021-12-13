```python
class Solution:
    def getMinimumDifference(self, root: Optional[TreeNode]) -> int:
        min_val = 100001
        pre = None
        
        def traversal(node):
            nonlocal min_val
            nonlocal pre
            
            if not node:
                return None
            traversal(node.left)
            if pre:
                min_val = min(min_val, abs(node.val - pre.val))
            pre = node
            traversal(node.right)
        
        traversal(root)
        
        return min_val
```
