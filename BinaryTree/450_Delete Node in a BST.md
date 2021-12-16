```python
class Solution:
    def deleteNode(self, root: Optional[TreeNode], key: int) -> Optional[TreeNode]:
        if not root:
            return None
        elif root.val == key:
            if root.left and root.right:
                cur = root.right
                while cur.left:
                    cur = cur.left
                cur.left = root.left
                return root.right
            elif root.left:
                return root.left
            elif root.right:
                return root.right
            else:
                return None
            
        root.left = self.deleteNode(root.left, key)
        root.right = self.deleteNode(root.right, key)
        
        return root
```
