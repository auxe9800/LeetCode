```python
class Solution:
    def minCameraCover(self, root: Optional[TreeNode]) -> int:
        self.num = 0
        if self.traversal(root) == 0:
            self.num += 1
        return self.num
    def traversal(self, node):
        if not node:
            return 2
        
        left = self.traversal(node.left)
        right = self.traversal(node.right)
        if left == 2 and right == 2:
            return 0
        if left == 0 or right == 0:
            self.num += 1
            return 1
        if left == 1 or right == 1: 
            return 2
```
