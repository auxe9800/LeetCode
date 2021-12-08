```python
class Solution:
    def pathSum(self, root: Optional[TreeNode], targetSum: int) -> List[List[int]]:
        if not root:
            return []
        res = []
        path = [root.val]
        self.travesal(root, path, res, targetSum - root.val)
        return res
    def travesal(self, cur, path, res, count):
        if not cur.left and not cur.right and count == 0:
            res.append(path.copy())
        if cur.left:
            path.append(cur.left.val)
            count -= cur.left.val
            self.travesal(cur.left, path, res, count)
            path.pop()
            count += cur.left.val
        if cur.right:
            path.append(cur.right.val)
            count -= cur.right.val
            self.travesal(cur.right, path, res, count)
            path.pop()
            count += cur.right.val
```
