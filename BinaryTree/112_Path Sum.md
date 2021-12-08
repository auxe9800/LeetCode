```python
class Solution:
    def hasPathSum(self, root: Optional[TreeNode], targetSum: int) -> bool:
        if not root:
            return False
        return self.travesal(root, targetSum - root.val)
    def travesal(self, node, count):
        if not node.left and not node.right and count == 0:
            return True
        if not node.left and not node.right:
            return False
        if node.left:
            count -= node.left.val
            if self.travesal(node.left, count):
                return True
            count += node.left.val
        if node.right:
            count -= node.right.val
            if self.travesal(node.right, count):
                return True
            count += node.right.val
```
