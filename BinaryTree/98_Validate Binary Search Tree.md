```python
class Solution:
    def isValidBST(self, root: Optional[TreeNode]) -> bool:
        cur_max = -float("INF")
        
        def traversal(root):
            nonlocal cur_max
            if not root:
                return True
            is_left_valid = traversal(root.left)
            if cur_max >= root.val:
                return False
            else:
                cur_max = root.val
            is_right_valid = traversal(root.right)
            return is_left_valid and is_right_valid
        return traversal(root)
```
