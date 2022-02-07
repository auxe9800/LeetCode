```python
class Solution:
    def rob(self, root: Optional[TreeNode]) -> int:
        result = self.robTree(root)
        return max(result)
    
    def robTree(self, cur):
        if not cur:
            return [0, 0]
        
        left = self.robTree(cur.left)
        right = self.robTree(cur.right)
        
        var1 = cur.val + left[1] + right[1]
        var2 = max(left[0], left[1]) + max(right[0], right[1])
        
        return [var1, var2]
```
