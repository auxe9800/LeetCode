```python
class Solution:
    def searchBST(self, root: Optional[TreeNode], val: int) -> Optional[TreeNode]:
        if not root:
            return None
        
        target = None
        if root.val == val:
            target = root
        elif root.val > val and root.left:
            target = self.searchBST(root.left, val)
        elif root.val < val and root.right:
            target = self.searchBST(root.right, val)
        return target
```
