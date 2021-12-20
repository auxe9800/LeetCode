```python
class Solution:
    def convertBST(self, root: Optional[TreeNode]) -> Optional[TreeNode]:
        pre = 0
        
        def traversal(cur):
            nonlocal pre
            if not cur:
                return None

            traversal(cur.right)
            cur.val += pre
            pre = cur.val
            traversal(cur.left)
                
        traversal(root)
        return root
```
