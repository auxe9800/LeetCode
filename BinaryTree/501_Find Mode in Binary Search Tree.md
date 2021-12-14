```python
class Solution:
    def __init__(self):
        self.pre = None
        self.count = 0
        self.max_count = 0
        self.res = []
    def findMode(self, root: Optional[TreeNode]) -> List[int]:
        if not root:
            return None
        self.BST(root)
        return self.res
    def BST(self, cur):
        if not cur:
            return None
        self.BST(cur.left)
        if not self.pre:
            self.count = 1
        elif self.pre.val == cur.val:
            self.count += 1
        else:
            self.count = 1
        self.pre = cur
            
        if self.count == self.max_count:
            self.res.append(cur.val)
        
        if self.count > self.max_count:
            self.max_count = self.count
            self.res = [cur.val]
        self.BST(cur.right)
```
