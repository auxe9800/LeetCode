```python
class Solution:
    def sumOfLeftLeaves(self, root: Optional[TreeNode]) -> int:
        if not root.left and not root.right:
            return 0
        total = []
        self.sumLeftLeaves(root, total)
        
        return sum(total)
    def sumLeftLeaves(self, node, total):
        if node.left:
            self.sumLeftLeaves(node.left, total)
        if node.right:
            self.sumLeftLeaves(node.right, total)
            if not node.right.left and not node.right.right:
                total.pop()
        if not node.left and not node.right:
            total.append(node.val)
```
