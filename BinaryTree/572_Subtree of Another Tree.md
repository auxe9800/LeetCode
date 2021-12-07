```python
class Solution:
    def isSubtree(self, root: Optional[TreeNode], subRoot: Optional[TreeNode]) -> bool:
        return self.dfs(root, subRoot)
    def dfs(self, root, subRoot):
        if root is None:
            return False
        return self.isSame(root, subRoot) or self.dfs(root.left, subRoot) or self.dfs(root.right, subRoot)
    def isSame(self, root, subRoot):
        if root is None and subRoot is not None:
            return False
        elif root is not None and subRoot is None:
            return False
        elif root is None and subRoot is None:
            return True
        elif root.val != subRoot.val:
            return False
        else:
            return self.isSame(root.left, subRoot.left) and self.isSame(root.right, subRoot.right)
```
