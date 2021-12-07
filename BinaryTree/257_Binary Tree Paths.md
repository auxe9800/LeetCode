```python
class Solution:
    def binaryTreePaths(self, root: Optional[TreeNode]) -> List[str]:
        path = ""
        result = []
        if not root:
            return result
        
        self.traversal(root, path, result)
        
        return result
    def traversal(self, root, path, result):
        path += str(root.val)
        
        if not root.left and not root.right:
            result.append(path)
            
        if root.left:
            self.traversal(root.left, path + "->", result)
            
        if root.right:
            self.traversal(root.right, path + "->", result)
```
